<template>
  <div class="bg-white shadow rounded-lg overflow-hidden">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl h-48 object-cover w-full"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam enim
        quasi tempore a sint. Sunt aliquam ab pariatur quia, incidunt, alias
        esse, accusamus illo veritatis maiores ratione vitae delectus cum!
      </p>
      <div class="flex items-center justify-between">
        <YouTubeButton :href="meal.strYoutube"> YouTube </YouTubeButton>
        <router-link
          to="/"
          class="px-3 py-2 rounded border-2 border-purple-600 hover:bg-purple-600 hover:text-white transition duration-300 ease-in-out"
          >View</router-link
        >
      </div>
    </div>
  </div>
</template>

<script setup>
import YouTubeButton from "./YouTubeButton.vue";
const { meal } = defineProps({
  meal: {
    type: Object,
    required: true,
  },
});
</script>
