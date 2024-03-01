<template>
  <div
    class="bg-gray-200 h-screen shadow-lg w-full md:w-72 border-r border-gray-300 md:flex flex-col justify-evenly items-center"
    :class="toggle ? 'absolute md:relative' : 'hidden '"
  >
    <button
      @click="$emit('close')"
      class="bg-gray-600 font-bold p-3 text-white rounded-full md:hidden"
    >
      Close
    </button>
    <p class="text-xl">Sidebar</p>
  </div>
</template>
<script setup>
const props = defineProps({
  toggle: Boolean,
});
</script>
