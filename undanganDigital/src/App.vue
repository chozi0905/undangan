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

const opened = ref(false)
const guestName = ref('Tamu Undangan')

onMounted(() => {
  const params = new URLSearchParams(window.location.search)
  if (params.get('to')) guestName.value = params.get('to')

  AOS.init({
    duration: 800,
    once: true
  })
})
</script>

<template>
  <Opening v-if="!opened" :name="guestName" @open="opened = true" />

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
