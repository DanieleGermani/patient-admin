<script setup>
import { reactive } from "vue";
import Alert from "./Alert.vue";
const patient = reactive({
  petName: "",
  ownwerName: "",
  email: "",
  entryDate: "",
  symptoms: "",
});
const alert = reactive({
  type: "",
  message: "",
});
const checkFormValidation = () => {
  if (Object.values(patient).includes("")) {
    alert.message = "Todos los campos son obligatorios";
    alert.type = "error";
    return;
  }
  alert.message = "Paciente registrado con exito";
  alert.type = "success";
};
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimineto Pacientes</h2>
    <p class="text-lg mt-5 text-center">
      Añade Pacientes y
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>

    <Alert v-if="alert.message" :alert="alert" />

    <form
      @submit.prevent="checkFormValidation"
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
    >
      <div class="mb-5">
        <label for="petName" class="block text-gray-700 uppercase font-bold">
          Nombre Mascota
        </label>
        <input
          id="petName"
          v-model="patient.petName"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          type="text"
          placeholder="Nombre de la mascota"
        />
      </div>
      <div class="mb-5">
        <label for="ownwerName" class="block text-gray-700 uppercase font-bold">
          Nombre Propietario
        </label>
        <input
          id="ownwerName"
          v-model="patient.ownwerName"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          type="text"
          placeholder="Nombre del propietario"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold">
          Email
        </label>
        <input
          id="email"
          v-model="patient.email"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          type="email"
          placeholder="Email Contacto Propietario"
        />
      </div>
      <div class="mb-5">
        <label for="entryDate" class="block text-gray-700 uppercase font-bold">
          Fecha alta
        </label>
        <input
          id="entryDate"
          v-model="patient.entryDate"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          type="date"
        />
      </div>
      <div class="mb-5">
        <label for="symptoms" class="block text-gray-700 uppercase font-bold">
          Sintomas
        </label>
        <textarea
          id="symptoms"
          v-model="patient.symptoms"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          placeholder="Describe los sintomas"
        />
      </div>
      <input
        type="submit"
        value="Registrar Paciente"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
      />
    </form>
  </div>
</template>
