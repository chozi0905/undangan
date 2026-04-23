<script setup>
import { ref } from 'vue'
const props = defineProps(['name'])
const msg = ref('')
</script>

<template>
  <section class="rsvp">
    <h2>Konfirmasi Kehadiran</h2>
    <textarea v-model="msg" placeholder="Tulis ucapan..." />

    <button @click="send">Kirim</button>
  </section>
</template>

<script>
export default {
  methods: {
    send() {
      const text = `Halo, saya ${this.name}. ${this.msg}`
      window.open(`https://wa.me/6289663566418?text=${encodeURIComponent(text)}`)
    }
  }
}
</script>

<style scoped>
.rsvp {
  padding: 40px;
  text-align: center;
}
textarea {
  width: 100%;
  border-radius: 10px;
  padding: 10px;
}
button {
  margin-top: 10px;
  padding: 12px;
  border-radius: 8px;
  background: #27ae60;
  color: white;
}
</style>