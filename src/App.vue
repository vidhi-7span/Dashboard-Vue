<script setup>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import gql from "graphql-tag";
import { useQuery } from "@vue/apollo-composable";
import { ref } from "vue";

const toggle = ref(true);
const COUNTRY_QUERY = gql`
  query Query {
    country(code: "BR") {
      name
      native
      capital
      emoji
      currency
      languages {
        code
        name
      }
    }
  }
`;
const { result, loading, error } = useQuery(COUNTRY_QUERY);
console.log("Result", result);
console.log("Loading", loading);
console.log("Error", error);
</script>

<template>
  <div class="flex relative">
    <Sidebar @close="toggle = false" :toggle="toggle"></Sidebar>
    <Header @open="toggle = true" v-slot="slotProps">
      {{ slotProps.text }}
    </Header>
  </div>
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
</template>
