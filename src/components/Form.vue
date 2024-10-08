<script setup></script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimineto Pacientes</h2>
    <p class="text-lg mt-5 text-center">
      Añade Pacientes y
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>

    <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10" action="">
      <div class="mb-5">
        <label for="pet" class="block text-gray-700 uppercase font-bold">
          Nombre Mascota
        </label>
        <input
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          id="pet"
          type="text"
          placeholder="Nombre de la mascota"
        />
      </div>
      <div class="mb-5">
        <label for="ownwer" class="block text-gray-700 uppercase font-bold">
          Nombre Propietario
        </label>
        <input
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          id="ownwer"
          type="text"
          placeholder="Nombre del propietario"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold">
          Email
        </label>
        <input
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          id="email"
          type="email"
          placeholder="Email Contacto Propietario"
        />
      </div>
      <div class="mb-5">
        <label for="entryDate" class="block text-gray-700 uppercase font-bold">
          Fecha alta
        </label>
        <input
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          id="entryDate"
          type="date"
        />
      </div>
      <div class="mb-5">
        <label for="symptoms" class="block text-gray-700 uppercase font-bold">
          Sintomas
        </label>
        <textarea
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          id="symptoms"
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
