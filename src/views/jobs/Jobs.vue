<script setup>
import { onMounted, ref } from 'vue';

const jobs = ref([])

async function fetchJobs() {
  try {
    const response = await fetch('http://localhost:3000/jobs')
    const result = await response.json()
    jobs.value = result
  } catch (error) {
    console.log(error.message)
  }
}

onMounted(() => {
  fetchJobs()
})
</script>
<template>
  <h1 class="my-4 text-6xl font-bold">Jobs List</h1>
  <div v-if="jobs.length" class="flex flex-wrap justify-center py-5">
    <router-link v-for="job in  jobs" :key="job.id" :to="{ name: 'JobDetails', params: { id: job.id } }"
      class="w-full max-w-sm p-6 mx-1 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700">
      <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ job.title }}</h5>
    </router-link>
  </div>
  <div v-else>
    <span class="py-5 text-lg font-semibold">Loading data ...</span>
  </div>
</template>
