<script setup>
import { computed } from "vue";
const props = defineProps({
  alert: {
    type: Object,
    required: true,
  },
});
const isError = computed(() => props.alert.type === "error");
</script>

<template>
  <div
    :class="[isError ? 'bg-red-500' : 'bg-green-500']"
    class="text-white text-center p-3 uppercase font-bold rounded-md mb-3"
  >
    {{ alert.message }}
  </div>
</template>
