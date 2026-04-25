<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

import Opening from './components/Opening.vue'
import Hero from './components/Hero.vue'
import Story from './components/Story.vue'
import Gallery from './components/Gallery.vue'
import RSVP from './components/RSVP.vue'
import Gift from './components/Gift.vue'
import Footer from './components/Footer.vue'
import MusicPlayer from './components/MusicPlayer.vue'
import petalImg from './assets/picture/kelopakBunga.png'

const opened = ref(false)
const guestName = ref('Tamu Undangan')
const petals = ref([])

let petalInterval = null
let petalIdCounter = 0

onMounted(() => {
  const params = new URLSearchParams(window.location.search)
  if (params.get('to')) guestName.value = params.get('to')

  AOS.init({
    duration: 800,
    once: true
  })
})

const addPetal = () => {
  petals.value.push({
    id: petalIdCounter++,
    left: Math.random() * 100,
    delay: Math.random() * 0.5,
    duration: 4 + Math.random() * 4,
    size: 15 + Math.random() * 20
  })
}

const removePetal = (id) => {
  const index = petals.value.findIndex(p => p.id === id)
  if (index > -1) {
    petals.value.splice(index, 1)
  }
}

const createPetals = () => {
  // Add initial batch
  for (let i = 0; i < 20; i++) {
    addPetal()
  }

  // Continue adding petals periodically
  petalInterval = setInterval(() => {
    if (petals.value.length < 50) {
      addPetal()
    }
  }, 300)
}

const handleOpen = () => {
  createPetals()
  opened.value = true
}

onUnmounted(() => {
  if (petalInterval) {
    clearInterval(petalInterval)
  }
})
</script>

<template>
  <!-- Falling Petals - outside sections -->
  <div class="petals-container">
    <img
      v-for="p in petals"
      :key="p.id"
      :src="petalImg"
      class="petal"
      :style="{
        left: p.left + '%',
        animationDelay: p.delay + 's',
        animationDuration: p.duration + 's',
        width: p.size + 'px'
      }"
      @animationend="removePetal(p.id)"
      alt=""
    />
  </div>

  <Opening v-if="!opened" :name="guestName" @open="handleOpen" />

  <div v-else>
    <Hero :name="guestName" />
    <Story />
    <Gallery />
    <RSVP :name="guestName" />
    <Gift />
    <Footer />
    <MusicPlayer :autoplay="true" />
  </div>
</template>

<style>
/* Falling Petals - global */
.petals-container {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9999;
  overflow: hidden;
}

.petal {
  position: absolute;
  top: -50px;
  animation: fall linear forwards;
  opacity: 0.8;
}

@keyframes fall {
  0% {
    top: -50px;
    transform: translateX(0) rotate(0deg);
  }
  100% {
    top: 110vh;
    transform: translateX(30px) rotate(360deg);
  }
}
</style>
