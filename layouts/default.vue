<template>
  <div>
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
  font-family: Muli, sans-serif;
}
</style>
