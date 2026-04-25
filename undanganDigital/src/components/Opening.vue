<script setup>
import bg from '@/assets/picture/background.png'
import photo from '@/assets/picture/pict6.jpeg'

defineProps(['name'])
const emit = defineEmits(['open'])
</script>

<template>
  <section class="opening" :style="{ backgroundImage: `url(${bg})` }">
    <div class="content">
      <!-- Decorative Frame -->
      <div class="frame-wrapper">
        <img :src="photo" class="photo" alt="Couple Photo" />
        <div class="frame-border"></div>

        <!-- Side Flourish - Left -->
        <svg class="flourish flourish-left" viewBox="0 0 40 120" fill="none">
          <path d="M20 0 C10 20, 30 40, 20 60 C10 80, 30 100, 20 120" stroke="#f0d78c" stroke-width="1.5" opacity="0.6" fill="none"/>
          <circle cx="20" cy="0" r="3" fill="#f0d78c" opacity="0.7"/>
          <circle cx="20" cy="30" r="2.5" fill="#f0d78c" opacity="0.6"/>
          <circle cx="20" cy="60" r="3" fill="#f0d78c" opacity="0.7"/>
          <circle cx="20" cy="90" r="2.5" fill="#f0d78c" opacity="0.6"/>
          <circle cx="20" cy="120" r="3" fill="#f0d78c" opacity="0.7"/>
        </svg>

        <!-- Side Flourish - Right -->
        <svg class="flourish flourish-right" viewBox="0 0 40 120" fill="none">
          <path d="M20 0 C30 20, 10 40, 20 60 C30 80, 10 100, 20 120" stroke="#f0d78c" stroke-width="1.5" opacity="0.6" fill="none"/>
          <circle cx="20" cy="0" r="3" fill="#f0d78c" opacity="0.7"/>
          <circle cx="20" cy="30" r="2.5" fill="#f0d78c" opacity="0.6"/>
          <circle cx="20" cy="60" r="3" fill="#f0d78c" opacity="0.7"/>
          <circle cx="20" cy="90" r="2.5" fill="#f0d78c" opacity="0.6"/>
          <circle cx="20" cy="120" r="3" fill="#f0d78c" opacity="0.7"/>
        </svg>
      </div>

      <!-- Text Section -->
      <div class="text-section">
        <!-- Top Ornament -->
        <div class="ornament-top">
          <div class="ornament-line"></div>
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483"/>
          </svg>
          <div class="ornament-line"></div>
        </div>

        <p class="overline">You're Invited To</p>
        <p class="above-name">Our Wedding</p>

        <h1 class="title">
          <span class="name">Gilang</span>
          <span class="ampersand">&amp;</span>
          <span class="name">Maya</span>
        </h1>

        <!-- Bottom Ornament -->
        <div class="ornament-bottom">
          <div class="ornament-line"></div>
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483"/>
          </svg>
          <div class="ornament-line"></div>
        </div>

        <!-- Guest Info -->
        <div class="guest-info">
          <p class="yth">Kepada Yth</p>
          <p class="guest-name">{{ name || 'Bapak/Ibu Tamu Undangan' }}</p>
        </div>
      </div>

      <!-- CTA Button -->
      <button class="btn" @click="emit('open')">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M5 12H19M19 12L12 5M19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <span>Buka Undangan</span>
      </button>
    </div>
  </section>
</template>

<style scoped>
.opening {
  min-height: 100vh;
  min-height: 100dvh;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.content {
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 50px 24px;
  width: 100%;
  max-width: 420px;
  gap: 24px;
}

/* Falling Petals */
.petals-container {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 100;
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

/* Frame & Photo */
.frame-wrapper {
  position: relative;
  width: 55%;
  max-width: 220px;
}

.photo {
  width: 100%;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  border-radius: 100px 100px 20px 20px;
  display: block;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
}

.frame-border {
  position: absolute;
  inset: -8px;
  border: 2px solid rgba(212, 180, 131, 0.7);
  border-radius: 108px 108px 28px 28px;
  pointer-events: none;
}

/* Side Flourishes */
.flourish {
  position: absolute;
  width: 30px;
  height: 100px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 3;
}

.flourish-left {
  left: -22px;
}

.flourish-right {
  right: -22px;
}

/* Text */
.text-section {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

/* Ornament */
.ornament-top,
.ornament-bottom {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  max-width: 200px;
}

.ornament-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, #d4b483, transparent);
}

.overline {
  font-family: 'Playfair Display', serif;
  font-size: clamp(11px, 3vw, 14px);
  letter-spacing: 4px;
  text-transform: uppercase;
  color: #a09080;
  font-weight: 500;
}

.above-name {
  font-family: 'Playfair Display', serif;
  font-size: clamp(13px, 3vw, 16px);
  color: #d4b483;
  letter-spacing: 2px;
}

.title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(36px, 10vw, 50px);
  color: #2c2c2c;
  line-height: 1.1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  flex-wrap: wrap;
  margin: 8px 0;
}

.name {
  font-family: 'Great Vibes', cursive !important;
  font-weight: 400;
  font-size: clamp(40px, 12vw, 60px);
}

.ampersand {
  font-family: 'Playfair Display', serif;
  font-size: 0.6em;
  color: #d4b483;
  font-style: italic;
}

/* Guest Info */
.guest-info {
  margin-top: 8px;
  padding: 16px 24px;
  background: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 12px;
}

.yth {
  font-family: 'Lato', sans-serif;
  font-size: clamp(10px, 2.5vw, 12px);
  color: #a09080;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 4px;
}

.guest-name {
  font-family: 'Playfair Display', serif;
  font-size: clamp(16px, 4vw, 22px);
  color: #2c2c2c;
  font-weight: 500;
  letter-spacing: 1px;
}

/* Button */
.btn {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  border-radius: 50px;
  border: 2px solid rgba(212, 180, 131, 0.6);
  background: transparent;
  color: #d4b483;
  font-family: 'Lato', sans-serif;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 0 20px rgba(212, 180, 131, 0.15);
  margin-top: 8px;
}

.btn:hover {
  background: rgba(212, 180, 131, 0.12);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px rgba(212, 180, 131, 0.3);
}

.btn:active {
  transform: translateY(0);
}

/* Responsive */
@media (max-width: 360px) {
  .content {
    padding: 40px 16px;
    gap: 20px;
  }

  .btn {
    padding: 14px 24px;
    font-size: 13px;
  }
}
</style>
