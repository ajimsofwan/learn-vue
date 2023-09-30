<script setup>
import { useRouter } from 'vue-router';
import ButtonPrimary from '../components/buttons/ButtonPrimary.vue'
const router = useRouter()

function redirect() {
  router.push('/')
}
</script>
<template>
  <h1 class="my-4 text-6xl font-bold">404 Not Found</h1>
  <p class="max-w-xl mx-auto text-base leading-relaxed text-gray-500 dark:text-gray-400 pb-5">The destination page is not
    found.
  </p>
  <ButtonPrimary @click="redirect">Home Page</ButtonPrimary>
</template>
