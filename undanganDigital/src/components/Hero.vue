<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import bgHero from '@/assets/picture/backgroundHero.png'

defineProps(['name'])

const targetDate = new Date('2026-12-20T08:00:00+07:00')

const timeLeft = ref({
  days: 0,
  hours: 0,
  minutes: 0,
  seconds: 0
})

let timer = null

const updateTimer = () => {
  const now = new Date()
  const diff = targetDate - now

  if (diff > 0) {
    timeLeft.value = {
      days: Math.floor(diff / (1000 * 60 * 60 * 24)),
      hours: Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)),
      minutes: Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60)),
      seconds: Math.floor((diff % (1000 * 60)) / 1000)
    }
  }
}

onMounted(() => {
  updateTimer()
  timer = setInterval(updateTimer, 1000)
})

onUnmounted(() => {
  clearInterval(timer)
})
</script>

<template>
  <section class="hero" :style="{ backgroundImage: `url(${bgHero})` }">
    <div class="overlay"></div>

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

      <!-- Countdown Timer -->
      <div class="countdown">
        <div class="countdown-item">
          <span class="countdown-num">{{ timeLeft.days }}</span>
          <span class="countdown-label">Hari</span>
        </div>
        <div class="countdown-sep">:</div>
        <div class="countdown-item">
          <span class="countdown-num">{{ String(timeLeft.hours).padStart(2, '0') }}</span>
          <span class="countdown-label">Jam</span>
        </div>
        <div class="countdown-sep">:</div>
        <div class="countdown-item">
          <span class="countdown-num">{{ String(timeLeft.minutes).padStart(2, '0') }}</span>
          <span class="countdown-label">Menit</span>
        </div>
        <div class="countdown-sep">:</div>
        <div class="countdown-item">
          <span class="countdown-num">{{ String(timeLeft.seconds).padStart(2, '0') }}</span>
          <span class="countdown-label">Detik</span>
        </div>
      </div>

      <!-- Event Cards -->
      <div class="event-cards">
        <!-- Akad -->
        <div class="event-card" data-aos="fade-up">
          <!-- Ring Icon -->
          <svg class="card-icon" width="48" height="48" viewBox="0 0 48 48" fill="none">
            <circle cx="24" cy="24" r="14" stroke="#d4b483" stroke-width="2" fill="none"/>
            <circle cx="24" cy="24" r="10" stroke="#d4b483" stroke-width="1.5" fill="none" opacity="0.5"/>
            <path d="M24 10 C24 10, 20 6, 16 10 C12 14, 16 20, 24 16 C32 20, 36 14, 32 10 C28 6, 24 10, 24 10" fill="#d4b483" opacity="0.6"/>
            <path d="M24 16 L24 10" stroke="#d4b483" stroke-width="2"/>
            <circle cx="24" cy="8" r="2" fill="#d4b483"/>
          </svg>

          <div class="card-ornament">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483"/>
            </svg>
          </div>
          <h2 class="event-title">Akad Nikah</h2>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <rect x="3" y="4" width="18" height="18" rx="2" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <path d="M3 10H21" stroke="#d4b483" stroke-width="1.5"/>
              <path d="M8 2V6M16 2V6" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
            <p class="event-date">Minggu, 20 Desember 2026</p>
          </div>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <circle cx="12" cy="12" r="9" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <path d="M12 7V12L16 14" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
            <p class="event-time">Pukul 08.00 WIB</p>
          </div>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2Z" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <circle cx="12" cy="9" r="2.5" stroke="#d4b483" stroke-width="1.5" fill="none"/>
            </svg>
            <p class="event-place">Kediaman Mempelai Wanita</p>
          </div>

          <p class="event-address">Jl. examples No. 123, Kota</p>
        </div>

        <!-- Resepsi -->
        <div class="event-card" data-aos="fade-up">
          <!-- Celebration Icon -->
          <svg class="card-icon" width="48" height="48" viewBox="0 0 48 48" fill="none">
            <path d="M24 6L26 14L34 14L28 19L30 27L24 22L18 27L20 19L14 14L22 14Z" fill="#d4b483" opacity="0.7"/>
            <circle cx="14" cy="30" r="4" fill="#d4b483" opacity="0.4"/>
            <circle cx="34" cy="30" r="4" fill="#d4b483" opacity="0.4"/>
            <path d="M14 34C14 37 17 39 20 39" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round" fill="none"/>
            <path d="M34 34C34 37 31 39 28 39" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round" fill="none"/>
            <path d="M24 34V40" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
            <path d="M20 40H28" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
          </svg>

          <div class="card-ornament">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483"/>
            </svg>
          </div>
          <h2 class="event-title">Resepsi</h2>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <rect x="3" y="4" width="18" height="18" rx="2" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <path d="M3 10H21" stroke="#d4b483" stroke-width="1.5"/>
              <path d="M8 2V6M16 2V6" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
            <p class="event-date">Minggu, 20 Desember 2026</p>
          </div>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <circle cx="12" cy="12" r="9" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <path d="M12 7V12L16 14" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
            <p class="event-time">Pukul 11.00 WIB - Selesai</p>
          </div>

          <div class="event-detail">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2Z" stroke="#d4b483" stroke-width="1.5" fill="none"/>
              <circle cx="12" cy="9" r="2.5" stroke="#d4b483" stroke-width="1.5" fill="none"/>
            </svg>
            <p class="event-place">Kediaman Mempelai Wanita</p>
          </div>

          <p class="event-address">Jl. examples No. 123, Kota</p>
        </div>
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

.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.25) 0%,
    rgba(255, 255, 255, 0.5) 30%,
    rgba(255, 255, 255, 0.85) 70%,
    rgba(255, 255, 255, 0.95) 100%
  );
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
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

/* Countdown Timer */
.countdown {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 8px 0;
}

.countdown-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 50px;
}

.countdown-num {
  font-family: 'Playfair Display', serif;
  font-size: clamp(22px, 6vw, 28px);
  color: #d4b483;
  font-weight: 500;
  line-height: 1;
}

.countdown-label {
  font-family: 'Lato', sans-serif;
  font-size: 10px;
  color: #8a8070;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-top: 4px;
}

.countdown-sep {
  font-family: 'Playfair Display', serif;
  font-size: clamp(18px, 5vw, 24px);
  color: #d4b483;
  font-weight: 500;
  margin-top: -4px;
}

/* Event Cards */
.event-cards {
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 100%;
  max-width: 340px;
  margin: 8px 0;
}

.event-card {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 16px;
  padding: 20px 24px;
  text-align: center;
  transition: all 0.3s ease;
}

.event-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 30px rgba(212, 180, 131, 0.15);
  border-color: rgba(212, 180, 131, 0.5);
}

.card-ornament {
  margin-bottom: 8px;
}

.card-icon {
  display: block;
  margin: 0 auto 8px;
}

.event-detail {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin: 6px 0;
}

.event-detail svg {
  flex-shrink: 0;
}

.event-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(18px, 5vw, 22px);
  color: #2c2c2c;
  font-weight: 500;
  margin-bottom: 10px;
}

.event-date {
  font-family: 'Lato', sans-serif;
  font-size: clamp(13px, 3vw, 15px);
  color: #5a5a5a;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.event-time {
  font-family: 'Lato', sans-serif;
  font-size: clamp(12px, 3vw, 14px);
  color: #d4b483;
  margin-top: 4px;
}

.event-place {
  font-family: 'Lato', sans-serif;
  font-size: clamp(11px, 3vw, 13px);
  color: #8a8070;
  margin-top: 8px;
}

.event-address {
  font-family: 'Lato', sans-serif;
  font-size: clamp(10px, 2.5vw, 12px);
  color: #a09080;
  margin-top: 2px;
}

/* Invitation Text */
.invite-text {
  font-family: 'Lato', sans-serif;
  font-size: clamp(13px, 3.5vw, 15px);
  color: #8a8070;
  letter-spacing: 1px;
  line-height: 1.8;
  margin-top: 4px;
}

/* Responsive */
@media (max-width: 360px) {
  .hero-content {
    padding: 40px 16px;
    gap: 16px;
  }

  .event-card {
    padding: 16px 20px;
  }
}
</style>
