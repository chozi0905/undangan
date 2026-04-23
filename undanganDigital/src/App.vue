<script setup>
import { ref, onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

import Opening from './components/Opening.vue'
import Hero from './components/Hero.vue'
import Event from './components/Event.vue'
import Gallery from './components/Gallery.vue'
import RSVP from './components/RSVP.vue'
import Footer from './components/Footer.vue'

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
  <Opening v-if="!opened" @open="opened = true" />

  <div v-else>
    <Hero :name="guestName" />
    <Event />
    <Gallery />
    <RSVP :name="guestName" />
    <Footer />
  </div>
</template>