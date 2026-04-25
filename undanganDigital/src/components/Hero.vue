<script setup>
import bgHero from '@/assets/picture/background1.png'

defineProps(['name'])
</script>

<template>
  <section class="hero" :style="{ backgroundImage: `url(${bgHero})` }">
    <div class="hero-content">
      <!-- Top Ornament -->
      <div class="ornament-top">
        <div class="line"></div>
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
          <path d="M10 1 L11.5 8.5 L19 10 L11.5 11.5 L10 19 L8.5 11.5 L1 10 L8.5 8.5 Z" fill="#d4b483"/>
        </svg>
        <div class="line"></div>
      </div>

      <!-- THE WEDDING OF -->
      <p class="wedding-of">THE WEDDING OF</p>

      <!-- Couple Name -->
      <h1 class="couple-name">
        <span class="name">Gilang</span>
        <span class="ampersand">&amp;</span>
        <span class="name">Maya</span>
      </h1>

      <!-- Bottom Ornament -->
      <div class="ornament-bottom">
        <div class="line"></div>
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
          <path d="M10 1 L11.5 8.5 L19 10 L11.5 11.5 L10 19 L8.5 11.5 L1 10 L8.5 8.5 Z" fill="#d4b483"/>
        </svg>
        <div class="line"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  min-height: 100dvh;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.hero-content {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 50px 24px;
  width: 100%;
  max-width: 420px;
}

/* Ornament */
.ornament-top,
.ornament-bottom {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  max-width: 260px;
}

.line {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, #d4b483, transparent);
}

/* THE WEDDING OF */
.wedding-of {
  font-family: 'Playfair Display', serif;
  font-size: clamp(14px, 4vw, 18px);
  color: #d4b483;
  letter-spacing: 6px;
  text-transform: uppercase;
  margin-top: 8px;
}

/* Couple Name */
.couple-name {
  font-family: 'Great Vibes', cursive;
  font-size: clamp(44px, 12vw, 68px);
  color: #2c2c2c;
  line-height: 1.2;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  flex-wrap: wrap;
  font-weight: 400;
  margin: 4px 0;
}

.ampersand {
  font-family: 'Playfair Display', serif;
  font-size: 0.5em;
  color: #d4b483;
  font-style: italic;
}

/* Responsive */
@media (max-width: 360px) {
  .hero-content {
    padding: 40px 16px;
    gap: 16px;
  }
}
</style>
