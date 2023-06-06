<template>
  <!-- <div class="p-8">
    <h1 class="text-4xl font-bold mb-4">Ingredients</h1>
    <router-link
      :to="{
        name: 'byIngredient',
        params: { ingredient: ingredient.idIngredient },
      }"
      v-for="ingredient of ingredients"
      :key="ingredient.id"
      class="bg-white shadow-md rounded-md p-4 mb-4 block"
    >
      <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
      <p>{{ ingredient.strDescription }}</p>
    </router-link>
  </div> -->
  <Meals :meals="meals" />
</template>

<script setup>
import axiosClient from "../AxiosClient";
import { onMounted, ref } from "vue";
import store from "../store";
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";

// const ingredients = ref([]);

// onMounted(() => {
//   axiosClient
//     .get("list.php?i=list")
//     .then(({ data }) => (ingredients.value = data.meals));
// });

const meals = computed(() => store.state.mealsByIngredient);
const route = useRoute();

onMounted(() =>
  store.dispatch("searchMealsByIngredient", route.params.ingredient)
);
</script>
