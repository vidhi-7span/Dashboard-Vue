<template>
  <div
    class="bg-gray-200 h-20 p-8 flex justify-between items-center w-full shadow-md border-b border-gray-300"
  >
    <button
      @click="$emit('open')"
      class="bg-gray-600 font-bold p-3 text-white rounded-full"
    >
      Open
    </button>
    <p class="text-xl">Header</p>
  </div>
</template>
<script setup></script>
