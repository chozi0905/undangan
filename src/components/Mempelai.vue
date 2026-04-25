<script setup>
import { ref, onMounted } from 'vue'

const visible = ref(false)

onMounted(() => {
  setTimeout(() => {
    visible.value = true
  }, 100)
})

// Data pengantin - bisa disesuaikan
const groom = {
  name: 'Gilang Raihansyah, S.Kom',
  father: 'Bpk. Uyi',
  mother: 'Ibu Supiyani',
  photo: null
}

const bride = {
  name: 'Maya Nursifa',
  father: 'Bpk. Asep S',
  mother: 'Ibu Eneng Suhaedah',
  photo: null
}
</script>

<template>
  <section class="mempelai">
    <!-- Background Decoration -->
    <div class="bg-decoration">
      <div class="deco-circle deco-1"></div>
      <div class="deco-circle deco-2"></div>
      <div class="deco-line deco-3"></div>
      <div class="deco-line deco-4"></div>
    </div>

    <!-- Gradient overlay -->
    <div class="bg-overlay"></div>

    <div class="mempelai-container" :class="{ visible }">
      <!-- Header with Quran Verse -->
      <div class="quran-header" data-aos="fade-down">
        <h2 class="quran-title">GM</h2>
        <div class="quran-verse">
          <p class="arabic">
            "Dan di antara tanda-tanda kekuasaan-Nya ialah Dia menciptakan untukmu
            pasangan dari jenismu sendiri, supaya kamu merasa tenteram kepadanya,
            dan dijadikan-Nya di antaramu mawaddah dan rahmah."
          </p>
          <p class="verse-ref">Surah Ar-Rum : 21</p>
        </div>
      </div>

      <!-- Couple Section -->
      <div class="couple-section">
        <!-- Groom -->
        <div class="person-card groom-card" data-aos="fade-right">
          <div class="card-label">Mempelai Pria</div>

          <div class="photo-placeholder">
            <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
              <circle cx="24" cy="18" r="10" stroke="#d4b483" stroke-width="2" fill="none"/>
              <path d="M10 42C10 32 16 26 24 26C32 26 38 32 38 42" stroke="#d4b483" stroke-width="2" fill="none"/>
            </svg>
          </div>

          <h3 class="person-name">{{ groom.name }}</h3>

          <div class="parents-info">
            <div class="parent">
              <span class="parent-icon">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                  <circle cx="12" cy="8" r="4" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                  <path d="M4 20C4 16 8 14 12 14C16 14 20 16 20 20" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                </svg>
              </span>
              <span>{{ groom.father }}</span>
            </div>
            <div class="parent">
              <span class="parent-icon">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                  <circle cx="12" cy="8" r="4" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                  <path d="M4 20C4 16 8 14 12 14C16 14 20 16 20 20" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                </svg>
              </span>
              <span>{{ groom.mother }}</span>
            </div>
          </div>
        </div>

        <!-- Center Divider -->
        <div class="center-divider" data-aos="zoom-in">
          <svg width="40" height="40" viewBox="0 0 40 40" fill="none">
            <circle cx="20" cy="20" r="18" stroke="#d4b483" stroke-width="1" fill="none" opacity="0.3"/>
            <path d="M20 4 L22 16 L34 20 L22 22 L20 34 L18 22 L6 20 L18 16 Z" fill="#d4b483"/>
          </svg>
        </div>

        <!-- Bride -->
        <div class="person-card bride-card" data-aos="fade-left">
          <div class="card-label">Mempelai Wanita</div>

          <div class="photo-placeholder">
            <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
              <circle cx="24" cy="18" r="10" stroke="#d4b483" stroke-width="2" fill="none"/>
              <path d="M10 42C10 32 16 26 24 26C32 26 38 32 38 42" stroke="#d4b483" stroke-width="2" fill="none"/>
            </svg>
          </div>

          <h3 class="person-name">{{ bride.name }}</h3>

          <div class="parents-info">
            <div class="parent">
              <span class="parent-icon">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                  <circle cx="12" cy="8" r="4" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                  <path d="M4 20C4 16 8 14 12 14C16 14 20 16 20 20" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                </svg>
              </span>
              <span>{{ bride.father }}</span>
            </div>
            <div class="parent">
              <span class="parent-icon">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                  <circle cx="12" cy="8" r="4" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                  <path d="M4 20C4 16 8 14 12 14C16 14 20 16 20 20" stroke="#d4b483" stroke-width="1.5" fill="none"/>
                </svg>
              </span>
              <span>{{ bride.mother }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Ornament -->
      <div class="bottom-ornament" data-aos="fade-up">
        <svg width="60" height="30" viewBox="0 0 60 30" fill="none">
          <path d="M0 15 L20 15 M40 15 L60 15" stroke="#d4b483" stroke-width="1"/>
          <path d="M30 5 L32 13 L40 15 L32 17 L30 25 L28 17 L20 15 L28 13 Z" fill="#d4b483"/>
        </svg>
      </div>
    </div>
  </section>
</template>

<style scoped>
.mempelai {
  padding: 80px 24px;
  background: url('@/assets/picture/background2.png') center/cover no-repeat;
  position: relative;
  overflow: hidden;
  display: flex;
  justify-content: center;
}

/* Background Decorations - Floral Pattern */
.bg-decoration {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.deco-circle {
  position: absolute;
  border-radius: 50%;
  opacity: 0.08;
  border: 2px solid #d4b483;
  background: transparent;
}

.deco-1 {
  width: 350px;
  height: 350px;
  top: -150px;
  left: -150px;
}

.deco-2 {
  width: 250px;
  height: 250px;
  bottom: -80px;
  right: -80px;
}

.deco-line {
  position: absolute;
  height: 1px;
  background: linear-gradient(to right, transparent, #d4b483, transparent);
  opacity: 0.15;
}

.deco-3 {
  width: 100%;
  top: 80px;
}

.deco-4 {
  width: 100%;
  bottom: 80px;
}

/* Extra decorative elements */
.deco-flower {
  position: absolute;
  width: 80px;
  height: 80px;
  opacity: 0.1;
  background: radial-gradient(circle, #d4b483 0%, transparent 70%);
  border-radius: 50%;
}

.deco-flower-1 {
  top: 20%;
  left: 10%;
}

.deco-flower-2 {
  top: 60%;
  right: 15%;
}

.deco-flower-3 {
  bottom: 25%;
  left: 20%;
}

/* Gradient overlay */
.bg-overlay {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse at top left, rgba(212, 180, 131, 0.15) 0%, transparent 50%),
    radial-gradient(ellipse at bottom right, rgba(248, 180, 196, 0.1) 0%, transparent 50%),
    radial-gradient(ellipse at center, rgba(255, 255, 255, 0.05) 0%, transparent 70%);
  pointer-events: none;
}

/* Container */
.mempelai-container {
  width: 100%;
  max-width: 800px;
  position: relative;
  z-index: 2;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.8s ease;
}

.mempelai-container.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Quran Header */
.quran-header {
  text-align: center;
  margin-bottom: 50px;
}

.quran-title {
  font-family: 'Great Vibes', cursive;
  font-size: clamp(32px, 8vw, 48px);
  color: #d4b483;
  margin-bottom: 20px;
}

.quran-verse {
  background: rgba(212, 180, 131, 0.1);
  border: 1px solid rgba(212, 180, 131, 0.25);
  border-radius: 16px;
  padding: 24px;
  max-width: 600px;
  margin: 0 auto;
}

.arabic {
  font-family: 'Lato', sans-serif;
  font-size: clamp(14px, 3.5vw, 16px);
  color: #d4b483;
  line-height: 1.8;
  font-style: italic;
  margin-bottom: 12px;
}

.verse-ref {
  font-family: 'Lato', sans-serif;
  font-size: 12px;
  color: #d4b483;
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* Couple Section */
.couple-section {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 30px;
  flex-wrap: wrap;
}

.person-card {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.95), rgba(248, 248, 252, 0.9));
  border-radius: 24px;
  padding: 32px;
  text-align: center;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(212, 180, 131, 0.2);
  transition: all 0.3s ease;
  flex: 1;
  min-width: 280px;
  max-width: 340px;
}

.person-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 50px rgba(212, 180, 131, 0.25);
}

.card-label {
  font-family: 'Playfair Display', serif;
  font-size: clamp(14px, 3vw, 16px);
  color: #b8976a;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.photo-placeholder {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(212, 180, 131, 0.2), rgba(248, 180, 196, 0.2));
  border: 3px solid rgba(212, 180, 131, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px;
}

.person-name {
  font-family: 'Great Vibes', cursive;
  font-size: clamp(28px, 6vw, 36px);
  color: #1a1a2e;
  margin-bottom: 16px;
}

.parents-info {
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding-top: 16px;
  border-top: 1px solid rgba(212, 180, 131, 0.25);
}

.parent {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  font-family: 'Lato', sans-serif;
  font-size: 13px;
  color: #4a4a4a;
}

.parent-icon {
  display: flex;
  align-items: center;
}

/* Center Divider */
.center-divider {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

/* Bottom Ornament */
.bottom-ornament {
  margin-top: 50px;
  display: flex;
  justify-content: center;
}

/* Responsive */
@media (max-width: 600px) {
  .couple-section {
    flex-direction: column;
  }

  .center-divider {
    transform: rotate(90deg);
  }

  .person-card {
    max-width: 100%;
  }

  .mempelai {
    padding: 60px 20px;
  }
}
</style>
