<template>
  <div>
    <Banner>
      <LuckafroFullIcon class="fill-current text-white" />
      <p class="text-white text-base text-center font-semibold px-8">
        Soy productor musical, tu mejor opción si quieres hacer instrumentales, mezcla y masterización
        de música urbana de alta calidad, con un sonido único y fresco.
      </p>
    </Banner>
    <div class="container mx-auto px-4">
      <section class="mt-8 py-5">
        <div class="block text-center mb-8">
          <h3 class="text-xl font-semibold tracking-widest uppercase text-gray-800">
            Servicios prestados
          </h3>
        </div>
        <div class="flex flex-wrap">
          <div class="w-full md:w-1/3 mb-4 md:px-2">
            <div class="border text-center rounded p-4 border-solid border-gray-400">
              <div class="flex justify-center">
                <img src="https://img.icons8.com/nolan/96/accordion.png">
              </div>
              <h3 class="block font-bold text-xl text-gray-900 mb-3">
                Instrumentales
              </h3>
              <p class="block text-gray-700 text-base">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit sed do eiusmod tempor.
              </p>
            </div>
          </div>
          <div class="w-full md:w-1/3 mb-4 md:px-2">
            <div class="border text-center rounded p-4 border-solid border-gray-400">
              <div class="flex justify-center">
                <img src="https://img.icons8.com/nolan/96/headphones.png">
              </div>
              <h3 class="block font-bold text-xl text-gray-900 mb-3">
                Mezcla
              </h3>
              <p class="block text-gray-700 text-base">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit sed do eiusmod tempor.
              </p>
            </div>
          </div>
          <div class="w-full md:w-1/3 mb-4 md:px-2">
            <div class="border text-center rounded p-4 border-solid border-gray-400">
              <div class="flex justify-center">
                <img src="https://img.icons8.com/nolan/96/audio-wave.png">
              </div>
              <h3 class="block font-bold text-xl text-gray-900 mb-3">
                Masterización
              </h3>
              <p class="block text-gray-700 text-base">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit sed do eiusmod tempor.
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Banner from '@/components/header/Banner'
import LuckafroFullIcon from '@/components/icons/LuckafroFullIcon'
export default {
  components: {
    Banner,
    LuckafroFullIcon
  }
}
</script>

<style>

</style>
