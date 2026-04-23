<script setup>
defineProps(['name'])
</script>

<template>
  <section class="hero">
    <p data-aos="fade-up">Kepada Yth</p>
    <h2 data-aos="fade-up">{{ name }}</h2>
    <h1 data-aos="zoom-in">Gilang & Maya</h1>
  </section>
</template>

<style scoped>
.hero {
  height: 100vh;
  background: linear-gradient(180deg, #ffffff, #e8fdf5);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
h1 {
  font-size: 2.5rem;
}
</style>