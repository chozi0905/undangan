<template>
  <section class="gallery">
    <h2 data-aos="fade-up">Gallery</h2>
    <div class="grid">
      <img v-for="i in 6" :key="i" :src="`https://picsum.photos/300/30${i}`" />
    </div>
  </section>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  padding: 20px;
}
img {
  width: 100%;
  border-radius: 12px;
}
</style>