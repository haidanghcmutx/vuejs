<template>
  <div class="p-8">
    <h1 class="text-4xl font-bold mb-4">Ingredients</h1>
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 bg-white border-gray-200 w-full mb-3"
      placeholder="Search for Ingredients"
      @change="searchMeals"
    />
    <router-link
      :to="{
        name: 'byIngredient',
        params: { ingredient: ingredient.strIngredient },
      }"
      v-for="ingredient of computedIngredients"
      :key="ingredient.idIngredient"
      class="bg-white shadow-md rounded-md p-4 mb-4 block"
    >
      <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
      <p>{{ ingredient.strDescription }}</p>
    </router-link>
  </div>
</template>

<script setup>
import { computed } from "@vue/reactivity";
import axiosClient from "../AxiosClient";
import { onMounted, ref } from "vue";

const ingredients = ref([]);
const keyword = ref("");
const computedIngredients = computed(() => {
  if (!computedIngredients) {
    return ingredients;
  }
  if (keyword.value) {
    return ingredients.value.filter((ingredient) =>
      ingredient.strIngredient
        .toLowerCase()
        .includes(keyword.value.toLowerCase())
    );
  } else {
    return ingredients.value;
  }
});

onMounted(() => {
  axiosClient
    .get("list.php?i=list")
    .then(({ data }) => (ingredients.value = data.meals));
});
</script>
