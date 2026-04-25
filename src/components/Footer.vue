<script setup>
import bgFooter from '@/assets/picture/background3.png'
</script>

<template>
  <footer class="footer" :style="{ backgroundImage: `url(${bgFooter})` }">
    <!-- Top Decoration -->
    <div class="footer-decoration">
      <svg width="80" height="40" viewBox="0 0 80 40" fill="none">
        <path d="M0 20 L30 20 M50 20 L80 20" stroke="#d4b483" stroke-width="1"/>
        <path d="M40 1 L42 18 L59 20 L42 22 L40 39 L38 22 L21 20 L38 18 Z" fill="#d4b483"/>
      </svg>
    </div>

    <!-- Closing Message -->
    <div class="closing-content">
      <p class="closing-title">Terima Kasih</p>
      <p class="closing-subtitle">Atas doa dan kehadiran Anda<br />dalam hari bahagia kami</p>

      <div class="couple-signature">
        <span class="signature">Gilang & Maya</span>
      </div>
    </div>

    <!-- Bottom Text -->
    <div class="footer-bottom">
      <p class="footer-text">Wassalamu'alaikum Wr. Wb.</p>
    </div>

    <!-- Credits -->
    <div class="credits">
      <p>Made with love for Gilang & Maya</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 60px 24px 40px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  position: relative;
}

/* Footer Decoration */
.footer-decoration {
  position: relative;
  margin-bottom: 30px;
}

/* Closing Content */
.closing-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

.closing-title {
  font-family: 'Great Vibes', cursive;
  font-size: clamp(36px, 10vw, 52px);
  color: #2c2c2c;
  line-height: 1.2;
}

.closing-subtitle {
  font-family: 'Lato', sans-serif;
  font-size: clamp(12px, 3vw, 14px);
  color: #8a8070;
  line-height: 1.8;
  letter-spacing: 0.5px;
  max-width: 300px;
}

.couple-signature {
  margin-top: 20px;
}

.signature {
  font-family: 'Great Vibes', cursive;
  font-size: clamp(28px, 8vw, 40px);
  color: #d4b483;
}

/* Footer Bottom */
.footer-bottom {
  margin-top: 40px;
  padding: 20px 0;
  border-top: 1px solid rgba(212, 180, 131, 0.2);
  width: 100%;
  max-width: 300px;
}

.footer-text {
  font-family: 'Lato', sans-serif;
  font-size: clamp(12px, 3vw, 14px);
  color: #a09080;
  letter-spacing: 1px;
}

/* Credits */
.credits {
  margin-top: 30px;
}

.credits p {
  font-family: 'Lato', sans-serif;
  font-size: 11px;
  color: #c0b8a8;
  letter-spacing: 0.5px;
}

/* Responsive */
@media (max-width: 360px) {
  .footer {
    padding: 50px 16px 30px;
  }
}
</style>
