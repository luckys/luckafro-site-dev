<template>
  <header class="bg-gray-900 p-3">
    <div class="flex items-center justify-between">
      <div class="flex items-center text-white mr-6">
        <LuckafroSquare class="fill-current h-10 w-10" />
        <span class="font-bold text-2xl tracking-tight ml-1">Luckafro</span>
      </div>
      <div class="block md:hidden">
        <button type="button" class="block text-gray-300 hover:text-white hover:border-white focus:outline-none" @click.prevent="isOpen = !isOpen">
          <ClearIcon v-if="isOpen" class="fill-current h-8 w-8" />
          <ReorderIcon v-else class="fill-current h-8 w-8" />
        </button>
      </div>
    </div>
    <div :class="[isOpen ? 'block' : 'hidden']">
      <a href="#" class="block py-1 text-white hover:text-indigo-500 font-semibold">Home</a>
      <a href="#" class="block py-1 text-white hover:text-indigo-500 font-semibold">Beats</a>
      <a href="#" class="block py-1 text-white hover:text-indigo-500 font-semibold">Services</a>
      <a href="#" class="block py-1 text-white hover:text-indigo-500 font-semibold">Blog</a>
      <a href="#" class="block py-1 text-white hover:text-indigo-500 font-semibold">Contact</a>
      <div class="block py-1">
        <button type="button" class="flex items-center" @click.prevent="lang = !lang">
          <SpainFlagIcon v-if="lang" class="h-6 w-6" />
          <EnglandFlagIcon v-else class="h-6 w-6" />
        </button>
      </div>
    </div>
  </header>
</template>

<script>
import ClearIcon from '@/components/icons/ClearIcon'
import EnglandFlagIcon from '@/components/icons/EnglandFlagIcon'
import LuckafroSquare from '@/components/icons/LuckafroSquare'
import ReorderIcon from '@/components/icons/ReorderIcon'
import SpainFlagIcon from '@/components/icons/SpainFlagIcon'
export default {
  name: 'Navbar',
  components: {
    ClearIcon,
    EnglandFlagIcon,
    LuckafroSquare,
    ReorderIcon,
    SpainFlagIcon
  },
  data () {
    return {
      isOpen: false,
      lang: true
    }
  }
}
</script>
