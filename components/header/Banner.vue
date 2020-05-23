<template>
  <div class="h-68 bg-indigo-700 flex items-center justify-center">
    <div class="z-0 md:z-10 h-68 home-img" />
    <div class="flex flex-col items-center px-4">
      <slot />
    </div>
  </div>
</template>

<script>
export default {

}
</script>
<style lang="css" scoped>
  .h-68 {
    height: 25rem;
  }
  .home-img {
    position: absolute;
    width: 100%;
    background-image: url('../../assets/images/banner/luckafro_optimized.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center center;
    opacity: 10%;
  }
</style>
