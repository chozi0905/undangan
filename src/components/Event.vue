<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const targetDate = new Date('2026-12-06T08:00:00+07:00')

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

// Ganti dengan link Google Maps lokasi pernikahan kamu
const locationUrl = 'https://maps.google.com/?q=Villa+17'
</script>

<template>
  <div class="event-section">
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

        <!-- Map Button -->
        <a :href="locationUrl" target="_blank" class="map-btn">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
            <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2Z" stroke="currentColor" stroke-width="2" fill="none"/>
            <circle cx="12" cy="9" r="3" stroke="currentColor" stroke-width="2" fill="none"/>
          </svg>
          Lihat Lokasi
        </a>
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

        <!-- Map Button -->
        <a :href="locationUrl" target="_blank" class="map-btn">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
            <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2Z" stroke="currentColor" stroke-width="2" fill="none"/>
            <circle cx="12" cy="9" r="3" stroke="currentColor" stroke-width="2" fill="none"/>
          </svg>
          Lihat Lokasi
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.event-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  width: 100%;
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

/* Map Button */
.map-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  margin-top: 16px;
  padding: 10px 20px;
  background: linear-gradient(135deg, #d4b483, #c8a870);
  color: white;
  border-radius: 25px;
  text-decoration: none;
  font-family: 'Lato', sans-serif;
  font-size: 13px;
  font-weight: 500;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(212, 180, 131, 0.3);
}

.map-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(212, 180, 131, 0.4);
}

/* Responsive */
@media (max-width: 360px) {
  .event-card {
    padding: 16px 20px;
  }
}
</style>
