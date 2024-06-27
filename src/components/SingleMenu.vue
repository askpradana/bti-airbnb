<script setup>
import { ref } from 'vue'

const image = ref('https://via.placeholder.com/400')
const title = ref('Cozy apartment in the city center')
const description = ref(
  'A nice and cozy apartment located in the heart of the city, close to all major attractions.'
)
const price = ref('$120/night')
const rating = ref('4.8/5')
</script>

<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg">
    <img class="w-full h-48 object-cover" :src="image" alt="Home image" />
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{ title }}</div>
      <p class="text-gray-700 text-base">{{ description }}</p>
    </div>
    <div class="px-6 pt-4 pb-2">
      <span
        class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
        >Price: {{ price }}</span
      >
      <span
        class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
        >Rating: {{ rating }}</span
      >
    </div>
  </div>
</template>
