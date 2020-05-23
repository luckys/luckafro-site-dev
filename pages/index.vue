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
      <section class="mt-8 py-5">
        <div class="block text-center mb-8">
          <h3 class="text-xl font-semibold tracking-widest uppercase text-gray-800">
            Instrumentales
          </h3>
        </div>
        <div class="flex flex-col">
          <div v-for="beat in beats" :key="beat.track_id" class="w-full rounded overflow-hidden shadow-md mb-4">
            <div class="flex flex-wrap">
              <div class="w-1/2">
                <img class="w-full h-32 p-3" :src="beat.details.artwork.default">
              </div>
              <div class="w-1/2">
                <h3 class="text-lg font-bold p-3">
                  {{ beat.details.title }}
                </h3>
                <div class="px-3">
                  <span v-for="tag in beat.details.tags.list" :key="tag.id" class="inline-block mr-2 mb-2 text-xs font-bold leading-sm uppercase p-2 text-center bg-indigo-700 text-white rounded-full">{{ tag.tag }}</span>
                </div>
              </div>
              <div class="p-3">
                <audio :id="beat.track_id" controls class="h-0 w-0 hidden">
                  <source :src="beat.details.stream_url">
                </audio>
                <div class="flex items-center w-full">
                  <div v-if="canPlay(beat.track_id)" @click.prevent="pauseTrack(beat.track_id)">
                    <PauseIcon class="fill-current text-indigo-900 w-10 h-10 cursor-pointer mr-4" />
                  </div>
                  <div v-else @click.prevent="playTrack(beat.track_id)">
                    <PlayIcon class="fill-current text-indigo-900 w-10 h-10 cursor-pointer mr-4" />
                  </div>
                  <div class=" relative w-32 h-2">
                    <progress id="seekObj" class="absolute w-32 h-2 border border-gray-500 bg-transparent rounded" :value="progressBarDuration" max="1" />
                    <div class="absolute -mt-1 w-4 h-4 bg-red-500 rounded-full cursor-pointer" />
                    <div v-if="canPlay(beat.track_id)" class="flex justify-between mt-3">
                      <p class="relative text-xs text-left text-gray-900">
                        {{ currentTime }}
                      </p>
                      <p class="relative text-xs text-left text-gray-900">
                        {{ totalDuration }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import { BEATSTARS_API } from '../utils/constants'
import Banner from '@/components/header/Banner'
import LuckafroFullIcon from '@/components/icons/LuckafroFullIcon'
import PauseIcon from '@/components/icons/PauseIcon'
import PlayIcon from '@/components/icons/PlayIcon'
export default {
  components: {
    Banner,
    LuckafroFullIcon,
    PauseIcon,
    PlayIcon
  },
  data () {
    return {
      beats: [],
      beatEvent: {
        isPlaying: false,
        beatId: null
      },
      player: null,
      progressBarDuration: 0
    }
  },
  computed: {
    totalDuration () {
      return this.calculateTotalValue(this.player.duration)
    },
    currentTime () {
      return this.calculateCurrentValue(this.player.currentTime)
    }
  },
  created () {
    this.fetchData()
  },
  methods: {
    async fetchData () {
      const { data } = await axios.get(BEATSTARS_API)
      this.beats = data.response.data.list
    },
    playTrack (trackId) {
      this.player = document.getElementById(trackId)
      this.player.play()
      this.beatEvent.isPlaying = true
      this.beatEvent.beatId = trackId
    },
    pauseTrack (trackId) {
      document.getElementById(trackId).pause()
      this.beatEvent.isPlaying = false
      this.beatEvent.beatId = trackId
    },
    canPlay (trackId) {
      return (this.beatEvent.isPlaying && this.beatEvent.beatId === trackId)
    },
    calculateTotalValue (length) {
      const minutes = Math.floor(length / 60)
      const secondsInt = length - minutes * 60
      const secondsStr = secondsInt.toString()
      const seconds = secondsStr.substr(0, 2)
      return minutes + ':' + seconds
    },
    calculateCurrentValue (currentTime) {
      const currentMinute = parseInt(currentTime / 60) % 60
      const currentSecondsLong = currentTime % 60
      const currentSeconds = currentSecondsLong.toFixed()
      return (currentMinute < 10 ? '0' + currentMinute : currentMinute) + ':' + (currentSeconds < 10 ? '0' + currentSeconds : currentSeconds)
    }
  }
}
</script>
<style lang="css" scoped>
progress::-webkit-progress-bar, progress::-moz-progress-bar {
  @apply bg-indigo-700
}
</style>
