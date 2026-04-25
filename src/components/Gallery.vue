<script setup>
import pict1 from '@/assets/picture/pict1.jpeg'
import pict2 from '@/assets/picture/pict2.jpeg'
import pict3 from '@/assets/picture/pict3.jpeg'
import pict4 from '@/assets/picture/pict4.jpeg'
import pict5 from '@/assets/picture/pict5.jpeg'
import pict6 from '@/assets/picture/pict6.jpeg'
import pict7 from '@/assets/picture/pict7.jpeg'
import pict8 from '@/assets/picture/pict8.jpeg'
import bgGallery from '@/assets/picture/background2.png'

const photos = [pict1, pict2, pict3, pict4, pict5, pict6, pict7, pict8]
</script>

<template>
  <section class="gallery" :style="{ backgroundImage: `url(${bgGallery})` }">
    <!-- Section Header -->
    <div class="section-header">
      <div class="header-ornament">
        <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
          <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>
          <path d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z" fill="#d4b483"/>
        </svg>
      </div>
      <h2 class="section-title">Gallery</h2>
      <p class="section-subtitle">Momen kebahagiaan kami</p>
    </div>

    <!-- Photo Grid -->
    <div class="photo-grid">
      <div
        v-for="(photo, index) in photos"
        :key="index"
        class="photo-item"
        :class="`photo-${index + 1}`"
        data-aos="fade-up"
      >
        <img :src="photo" :alt="`Photo ${index + 1}`" />
      </div>
    </div>

    <!-- Bottom Decoration -->
    <div class="bottom-decoration">
      <svg width="60" height="30" viewBox="0 0 60 30" fill="none">
        <path d="M0 15 L20 15 M40 15 L60 15" stroke="#d4b483" stroke-width="1"/>
        <path d="M30 5 L32 13 L40 15 L32 17 L30 25 L28 17 L20 15 L28 13 Z" fill="#d4b483"/>
      </svg>
    </div>
  </section>
</template>

<style scoped>
.gallery {
  padding: 60px 24px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

/* Section Header */
.section-header {
  text-align: center;
  margin-bottom: 40px;
}

.header-ornament {
  margin-bottom: 12px;
}

.section-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(24px, 6vw, 32px);
  color: #2c2c2c;
  font-weight: 500;
  margin-bottom: 8px;
}

.section-subtitle {
  font-family: 'Lato', sans-serif;
  font-size: clamp(12px, 3vw, 14px);
  color: #8a8070;
  letter-spacing: 1px;
}

/* Photo Grid - Masonry style */
.photo-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(4, auto);
  gap: 12px;
  width: 100%;
  max-width: 500px;
}

.photo-item {
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
  transition: all 0.3s ease;
  opacity: 1;
}

.photo-item:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 24px rgba(212, 180, 131, 0.25);
  opacity: 1;
}

.photo-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease;
}

.photo-item:hover img {
  transform: scale(1.05);
}

/* Varying heights for masonry effect */
.photo-1 { aspect-ratio: 3 / 4; }
.photo-2 { aspect-ratio: 4 / 3; }
.photo-3 { aspect-ratio: 1 / 1; }
.photo-4 { aspect-ratio: 4 / 3; }
.photo-5 { aspect-ratio: 3 / 4; }
.photo-6 { aspect-ratio: 1 / 1; }
.photo-7 { aspect-ratio: 4 / 3; }
.photo-8 { aspect-ratio: 3 / 4; }

/* Bottom Decoration */
.bottom-decoration {
  position: relative;
  z-index: 2;
  margin-top: 50px;
}

/* Responsive */
@media (max-width: 360px) {
  .gallery {
    padding: 50px 16px;
  }

  .photo-grid {
    gap: 8px;
  }
}
</style>
