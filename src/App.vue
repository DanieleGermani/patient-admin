<script setup>
import { ref, reactive, watch, onMounted } from "vue";
import { uid } from "uid";
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Patient from "./components/Patient.vue";

const patients = ref([]);

const patient = reactive({
  id: null,
  petName: "",
  ownwerName: "",
  email: "",
  entryDate: "",
  symptoms: "",
});

onMounted(() => {
  getPatientsFromLocalStorage();
});

watch(
  patients,
  () => {
    setPatientInLocalStorage();
  },
  { deep: true }
);

const setPatientInLocalStorage = () => {
  localStorage.setItem("patients", JSON.stringify(patients.value));
};

const getPatientsFromLocalStorage = () => {
  if (localStorage.getItem("patients")) {
    patients.value = JSON.parse(localStorage.getItem("patients"));
  }
};

const savePatient = () => {
  if (patient.id) {
    const index = patients.value.findIndex((item) => item.id === patient.id);
    patients.value[index] = { ...patient };
  } else {
    patients.value.push({ ...patient, id: uid() });
  }
  // Clean Form
  Object.assign(patient, {
    id: null,
    petName: "",
    ownwerName: "",
    email: "",
    entryDate: "",
    symptoms: "",
  });
};

const updatePatient = (patientToUpdate) => {
  Object.assign(patient, patientToUpdate);
};

const deletePatient = (id) => {
  patients.value = patients.value.filter((patient) => patient.id !== id);
};
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Form
        v-model:petName="patient.petName"
        v-model:ownwerName="patient.ownwerName"
        v-model:email="patient.email"
        v-model:entryDate="patient.entryDate"
        v-model:symptoms="patient.symptoms"
        :id="patient.id"
        @save-patient="savePatient"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Listado de Pacientes</h3>

        <div v-if="patients.length > 0">
          <p class="text-lg mt-5 text-center">
            Informacins de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>
          <Patient
            v-for="patient in patients"
            :key="patient.id"
            :patient="patient"
            @update-patient="updatePatient"
            @delete-patient="deletePatient"
          />
        </div>
        <p v-else class="mt-10 text-center text-2xl">No hay Pacientes</p>
      </div>
    </div>
  </div>
</template>
