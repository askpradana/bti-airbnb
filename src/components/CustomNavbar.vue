<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { CircleUserIcon, Globe, Triangle, Menu } from 'lucide-vue-next'

const showMenu = ref(true)
const search = ref('')
let lastScrollY = window.scrollY

const handleScroll = () => {
  const currentScrollY = window.scrollY
  showMenu.value = currentScrollY < lastScrollY || currentScrollY === 0
  lastScrollY = currentScrollY
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s linear;
}
.slide-enter,
.slide-leave-to {
  transform: translateY(-100%);
  opacity: 0;
}
</style>

<template>
  <div>
    <div class="fixed top-0 left-0 right-0 z-50 bg-white shadow-lg py-4">
      <div class="container mx-auto flex justify-between items-center">
        <div class="text-xl font-bold flex flex-row gap-4 justify-center items-center">
          <Triangle />
          Airbnb
        </div>
        <div class="flex flex-col gap-4 items-center space-x-4">
          <transition name="slide">
            <nav v-if="showMenu" class="flex space-x-4">
              <a href="#" class="ml-4 text-gray-700">Tempat menginap</a>
              <a href="#" class="ml-4 text-gray-700">Pengalaman</a>
              <a href="#" class="ml-4 text-gray-700">Pengalaman Online</a>
            </nav>
          </transition>
          <input
            v-model="search"
            type="text"
            placeholder="Search"
            class="py-2 px-4 border border-gray-300 rounded-full focus:w-96 focus:outline-none"
          />
        </div>
        <div class="flex flex-row gap-4 items-center">
          <p class="font-semibold cursor-pointer hidden lg:block">Jadikan rumah anda Airbnb</p>
          <Globe />
          <div class="border-gray-400 border-2 px-4 py-2 rounded-full flex flex-row gap-4">
            <Menu />
            <CircleUserIcon />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
