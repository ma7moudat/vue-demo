<script setup>
import {onMounted, reactive} from "vue";

const request = reactive({
  data: null,
  error: null,
  loading: false,
})

onMounted(() => {
  request.data = null
  request.loading = true
  request.error = null
  fetch('https://dummyjson.com/quotes/random')
    .then((response) => response.json())
    .then((json) => {
      request.data = json
      request.loading = false
    })
    .catch((err) => {
      request.loading = false
      request.error = err
    })
})
</script>

<template>
  <div class="about">
    <h1>Quote of the day:</h1>

    <pre>{{ request }}</pre>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
