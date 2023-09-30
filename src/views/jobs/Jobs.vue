<script setup>
import { ref } from 'vue';

const data = ref([
  { id: 1, title: "Front-End Developer", detail: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Minima, quis!" },
  { id: 2, title: "Back-End Developer", detail: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Minima, quis!" },
  { id: 3, title: "UX/UI Designer", detail: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Minima, quis!" }
])

const jobs = data.value

</script>
<template>
  <h1 class="my-4 text-6xl font-bold">Jobs List</h1>
  <div class="flex flex-wrap justify-center py-5">
    <router-link v-for="job in  jobs" :key="job.id" :to="{ name: 'JobDetails', params: { id: job.id } }"
      class="w-full max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700 mx-1">
      <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ job.title }}</h5>
    </router-link>
  </div>
</template>
