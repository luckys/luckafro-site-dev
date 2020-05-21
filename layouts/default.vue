<template>
  <div class="mx-auto">
    <Navbar />
    <nuxt />
  </div>
</template>

<script>
import Navbar from '@/components/navbar/Navbar'
export default {
  components: {
    Navbar
  }
}
</script>

<style>
html {
  font-family: Roboto, sans-serif;
}
</style>
