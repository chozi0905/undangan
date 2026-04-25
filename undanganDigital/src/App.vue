<script setup>
import { ref, onMounted } from 'vue'
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

onMounted(() => {
  const params = new URLSearchParams(window.location.search)
  if (params.get('to')) guestName.value = params.get('to')

  AOS.init({
    duration: 800,
    once: true
  })
})

const createPetals = () => {
  for (let i = 0; i < 30; i++) {
    petals.value.push({
      id: Date.now() + i,
      left: Math.random() * 100,
      delay: Math.random() * 2,
      duration: 3 + Math.random() * 3,
      rotate: Math.random() * 360,
      size: 15 + Math.random() * 20
    })
  }

  setTimeout(() => {
    petals.value = []
  }, 5 * 60 * 1000)
}

const handleOpen = () => {
  createPetals()
  opened.value = true
}
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
        width: p.size + 'px',
        transform: 'rotate(' + p.rotate + 'deg)'
      }"
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
    opacity: 0.8;
  }
  100% {
    top: 110vh;
    opacity: 0;
  }
}
</style>
