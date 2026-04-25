<script setup>
import { ref } from 'vue'
import bgGift from '@/assets/picture/background2.png'

const copied = ref(null)

const accounts = [
  {
    id: 'BSI',
    bank: 'Bank Syariah Indonesia',
    account: '7311760488',
    name: 'MAYA NURSIFA',
    icon: 'M3 7H21V17H3V7ZM3 7V5H21V7M3 17V19H21V17'
  },
  {
    id: 'BSI',
    bank: 'Bank Syariah Indonesia',
    account: '7194792580',
    name: 'GILANG RAIHANSYAH',
    icon: 'M3 7H21V17H3V7ZM3 7V5H21V7M3 17V19H21V17'
  },
  {
    id: 'dana',
    bank: 'DANA',
    account: '08558996478',
    name: 'Maya Nursifa',
    icon: 'M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM12 20C7.59 20 4 16.41 4 12C4 7.59 7.59 4 12 4C16.41 4 20 7.59 20 12C20 16.41 16.41 20 12 20ZM12 6C8.69 6 6 8.69 6 12C6 15.31 8.69 18 12 18C15.31 18 18 15.31 18 12C18 8.69 15.31 6 12 6ZM12 16C9.79 16 8 14.21 8 12C8 9.79 9.79 8 12 8C14.21 8 16 9.79 16 12C16 14.21 14.21 16 12 16Z'
  }
]

const copyToClipboard = async (text, id) => {
  try {
    await navigator.clipboard.writeText(text)
    copied.value = id
    setTimeout(() => {
      copied.value = null
    }, 2000)
  } catch (err) {
    console.error('Failed to copy:', err)
  }
}
</script>

<template>
  <section class="gift" :style="{ backgroundImage: `url(${bgGift})` }">
    <!-- Section Header -->
    <div class="section-header">
      <div class="header-ornament">
        <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
          <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>
          <path d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z" fill="#d4b483"/>
        </svg>
      </div>
      <h2 class="section-title">Wedding Gift</h2>
      <p class="section-subtitle">Kehadiran Anda merupakan hadiah terindah<br />Namun jika Anda ingin berkonfirmasi</p>
    </div>

    <!-- Gift Cards -->
    <div class="gift-cards">
      <div
        v-for="acc in accounts"
        :key="acc.id"
        class="gift-card"
        data-aos="fade-up"
      >
        <div class="card-header">
          <span class="bank-name">{{ acc.bank }}</span>
        </div>

        <div class="card-body">
          <p class="account-number">{{ acc.account }}</p>
          <p class="account-name">{{ acc.name }}</p>
        </div>

        <button class="copy-btn" @click="copyToClipboard(acc.account, acc.id)">
          <svg v-if="copied !== acc.id" width="16" height="16" viewBox="0 0 24 24" fill="none">
            <rect x="9" y="9" width="13" height="13" rx="2" stroke="currentColor" stroke-width="2"/>
            <path d="M5 15H4C2.89543 15 2 14.1046 2 13V4C2 2.89543 2.89543 2 4 2H13C14.1046 2 15 2.89543 15 4V5" stroke="currentColor" stroke-width="2"/>
          </svg>
          <svg v-else width="16" height="16" viewBox="0 0 24 24" fill="none">
            <path d="M20 6L9 17L4 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <span>{{ copied === acc.id ? 'Tersalin!' : 'Salin' }}</span>
        </button>
      </div>
    </div>

    <!-- Physical Gift Info -->
    <div class="physical-gift" data-aos="fade-up">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
        <path d="M21 8V21H3V8M1 3H23V8H1V3ZM21 8H3M1 3V8M21 8L22 3H2L3 8" stroke="#d4b483" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
      <div class="physical-text">
        <p class="physical-title">Hadiah Fisik</p>
        <p class="physical-address">Bisa dikirimkan ke alamat acara pernikahan</p>
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
.gift {
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
  position: relative;
  z-index: 2;
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
  line-height: 1.7;
}

/* Gift Cards */
.gift-cards {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 380px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.gift-card {
  background: rgba(255, 255, 255, 0.95);
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 16px;
  padding: 20px 24px;
  display: flex;
  align-items: center;
  gap: 16px;
  transition: all 0.3s ease;
}

.gift-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(212, 180, 131, 0.15);
  border-color: rgba(212, 180, 131, 0.5);
}

.card-header {
  display: flex;
  flex-direction: column;
  min-width: 90px;
}

.bank-name {
  font-family: 'Playfair Display', serif;
  font-size: clamp(14px, 3.5vw, 16px);
  color: #2c2c2c;
  font-weight: 500;
}

.card-body {
  flex: 1;
  text-align: left;
}

.account-number {
  font-family: 'Lato', sans-serif;
  font-size: clamp(14px, 3.5vw, 16px);
  color: #2c2c2c;
  font-weight: 500;
  letter-spacing: 1px;
}

.account-name {
  font-family: 'Lato', sans-serif;
  font-size: clamp(11px, 2.5vw, 12px);
  color: #8a8070;
  margin-top: 2px;
}

.copy-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  border-radius: 20px;
  border: 1px solid #d4b483;
  background: transparent;
  color: #d4b483;
  font-family: 'Lato', sans-serif;
  font-size: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.copy-btn:hover {
  background: rgba(212, 180, 131, 0.15);
}

/* Physical Gift */
.physical-gift {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 30px;
  padding: 16px 24px;
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid rgba(212, 180, 131, 0.25);
  border-radius: 12px;
  max-width: 380px;
  width: 100%;
}

.physical-text {
  text-align: left;
}

.physical-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(13px, 3vw, 15px);
  color: #2c2c2c;
  font-weight: 500;
}

.physical-address {
  font-family: 'Lato', sans-serif;
  font-size: clamp(11px, 2.5vw, 12px);
  color: #8a8070;
  margin-top: 2px;
}

/* Bottom Decoration */
.bottom-decoration {
  position: relative;
  z-index: 2;
  margin-top: 50px;
}

/* Responsive */
@media (max-width: 360px) {
  .gift {
    padding: 50px 16px;
  }

  .gift-card {
    flex-direction: column;
    text-align: center;
  }

  .card-body {
    text-align: center;
  }

  .copy-btn {
    width: 100%;
    justify-content: center;
  }
}
</style>
