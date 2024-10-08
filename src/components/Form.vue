<script setup>
import { reactive, computed } from "vue";
import Alert from "./Alert.vue";
const alert = reactive({
  type: "",
  message: "",
});

const emit = defineEmits([
  "update:petName",
  "update:ownwerName",
  "update:email",
  "update:entryDate",
  "update:symptoms",
  "save-patient",
]);

const props = defineProps({
  id: {
    type: [String, null],
  },
  petName: {
    type: String,
  },
  ownwerName: {
    type: String,
  },
  email: {
    type: String,
  },
  entryDate: {
    type: String,
  },
  symptoms: {
    type: String,
  },
});
const checkFormValidation = () => {
  if (Object.values(props).includes("")) {
    alert.message = "Todos los campos son obligatorios";
    alert.type = "error";
    return;
  }
  emit("save-patient");
  alert.message = "Paciente registrado con exito";
  alert.type = "success";
  setTimeout(() => {
    Object.assign(alert, {
      type: "",
      message: "",
    });
  }, 3000);
};

const edit = computed(() => props.id);
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
          @input="$emit('update:petName', $event.target.value)"
          :value="petName"
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
          @input="$emit('update:ownwerName', $event.target.value)"
          :value="ownwerName"
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
          @input="$emit('update:email', $event.target.value)"
          :value="email"
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
          @input="$emit('update:entryDate', $event.target.value)"
          :value="entryDate"
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
          @input="$emit('update:symptoms', $event.target.value)"
          :value="symptoms"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          placeholder="Describe los sintomas"
        />
      </div>
      <input
        type="submit"
        :value="[edit ? 'Guardar cambios' : 'Registrar Paciente']"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
      />
    </form>
  </div>
</template>
