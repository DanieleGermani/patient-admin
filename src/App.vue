<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Patient from "./components/Patient.vue";

const patients = ref([]);

const patient = reactive({
  petName: "",
  ownwerName: "",
  email: "",
  entryDate: "",
  symptoms: "",
});

const savePatient = () => {
  patients.value.push(patient);
  console.log(patients.value);
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
          />
        </div>
        <p v-else class="mt-10 text-center text-2xl">No hay Pacientes</p>
      </div>
    </div>
  </div>
</template>
