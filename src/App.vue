<script setup>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import { ref } from "vue";

const toggle = ref(true);
</script>
<template>
  <div class="flex">
    <Sidebar v-if="toggle" @close="toggle = false"></Sidebar>
    <Header @open="toggle = true"> </Header>
  </div>
</template>
