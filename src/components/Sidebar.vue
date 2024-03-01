<template>
  <div
    class="bg-gray-200 w-72 h-screen shadow-lg border-r border-gray-300 flex flex-col justify-evenly items-center"
  >
    <button
      @click="$emit('close')"
      class="bg-gray-600 font-bold p-3 text-white rounded-full"
    >
      Close
    </button>
    <p class="text-xl">Sidebar</p>
  </div>
</template>
