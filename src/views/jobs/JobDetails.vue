<script setup>
import { onMounted, ref } from 'vue';


const props = defineProps(['id'])
const job = ref(null)

async function fetchJob() {
  try {
    const response = await fetch('http://localhost:3000/jobs/' + props.id)
    const result = await response.json()
    job.value = result
  } catch (error) {
    console.log(error.message)
  }
}

onMounted(() => {
  fetchJob()
})
</script>
<template>
  <div v-if="job">
    <h1 class="my-4 text-6xl font-bold">{{ job.title }}</h1>
    <p class="max-w-xl mx-auto text-base leading-relaxed text-gray-500 dark:text-gray-400">
      {{ job.detail }}
    </p>
  </div>
  <div v-else>
    <span class="py-5 text-lg font-semibold">Loading data ...</span>
  </div>
</template>
