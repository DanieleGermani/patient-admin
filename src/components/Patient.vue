<script setup>
defineEmits(["update-patient", "delete-patient"]);
const props = defineProps({
  patient: {
    type: Object,
    required: true,
  },
});
</script>
<template>
  <div class="mx-5 my-10 bg-white shadow-md px-5 py-10 rounded-xl">
    <p class="font-bold mb-3 text-gray-700 uppercase">
      ID:
      <span class="font-normal normal-case"> {{ patient.id }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Nombre:
      <span class="font-normal normal-case"> {{ patient.petName }} </span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Propietario:
      <span class="font-normal normal-case"> {{ patient.ownwerName }} </span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Email:
      <span class="font-normal normal-case"> {{ patient.email }} </span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Fecha Alta:
      <span class="font-normal normal-case"> {{ patient.entryDate }} </span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Síntomas:
      <span class="font-normal normal-case"> {{ patient.symptoms }} </span>
    </p>

    <div class="grid md:grid-cols-2 gap-5 mt-10">
      <button
        @click="$emit('update-patient', patient)"
        type="button"
        class="block w-full py-2 px-10 bg-indigo-600 hover:bg-indigo-700 text-white font-bold uppercase rounded-lg"
      >
        Editar
      </button>

      <button
        @click="$emit('delete-patient', patient.id)"
        type="button"
        class="block w-full py-2 px-10 bg-red-600 hover:bg-red-700 text-white font-bold uppercase rounded-lg"
      >
        Eliminar
      </button>
    </div>
  </div>
</template>
