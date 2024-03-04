<script setup>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import { useQuery } from "@vue/apollo-composable";
import { ref } from "vue";
import CountryQuery from "./graph/country.gql";
const toggle = ref(true);

const { result, loading, error } = useQuery(CountryQuery);
// console.log("Result", result);
// console.log("Loading", loading);
// console.log("Error", error);
</script>

<template>
  <div class="flex relative w-full">
    <Sidebar @close="toggle = false" :toggle="toggle"></Sidebar>
    <div>
      <Header @open="toggle = true" v-slot="slotProps" class="w-full">
        {{ slotProps.text }}
      </Header>
      <div class="w-full">
        <p v-if="error">Something went wrong...</p>
        <p v-if="loading">Loading...</p>
        <div v-else>
          <p>{{ result.country.name }}</p>
          <p>{{ result.country.native }}</p>
          <p>{{ result.country.capital }}</p>
          <p>{{ result.country.emoji }}</p>
          <p>{{ result.country.currency }}</p>
          <p v-for="language in result.country.languages" :key="language.code">
            {{ language.name }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
