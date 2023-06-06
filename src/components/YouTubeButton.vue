<template>
  <a
    :href="href"
    target="_blank"
    class="px-3 py-2 cursor-pointer rounded border-2 border-red-600 hover:bg-red-600 hover:text-white transition duration-300 ease-in-out"
    ><slot></slot
  ></a>
</template>

<script setup>
const props = defineProps({
  href: {
    type: String,
    required: true,
  },
});
</script>
