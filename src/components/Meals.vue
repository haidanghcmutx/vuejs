<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>

  <div v-if="!meals?.length" class="flex justify-center text-gray-600">
    The is Nothing to Show
  </div>
</template>

<script setup>
import MealItem from "./MealItem.vue";
import { defineProps } from "vue";

const { meals } = defineProps({
  meals: {
    type: Array,
    required: true,
  },
});
</script>
