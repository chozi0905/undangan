<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import bgRsvp from '@/assets/picture/background2.png'

const props = defineProps(['name'])

let observer = null
const visible = ref(false)

const guestName = ref('')
const message = ref('')
const attendance = ref('hadir')
const guestCount = ref(1)

onMounted(() => {
  const section = document.querySelector('.rsvp')
  observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      visible.value = entry.isIntersecting
    })
  }, { threshold: 0.2 })
  if (section) observer.observe(section)
})

onUnmounted(() => {
  if (observer) observer.disconnect()
})

const sendToWhatsApp = () => {
  const finalName = guestName.value || props.name || 'Tamu Undangan'
  const greeting = `Hallo, saya ${finalName}.`
  const hadirText = attendance.value === 'hadir' ? 'Berdiri hadir' : 'Maaf, tidak bisa hadir'
  const text = `${greeting}

Dengan ini saya ${hadirText} dalam acara pernikahan Gilang & Maya.

Jumlah tamu: ${guestCount.value} orang

Ucapan:
${message.value || '(tidak ada ucapan)'}

--
Dikirim dari Undangan Digital`

  window.open(`https://wa.me/6289663566418?text=${encodeURIComponent(text)}`)
}
</script>

<template>
  <section class="rsvp" :style="{ backgroundImage: `url(${bgRsvp})` }" :class="{ visible }">
    <!-- Section Header -->
    <div class="section-header">
      <div class="header-ornament">
        <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
          <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>
          <path d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z" fill="#d4b483"/>
        </svg>
      </div>
      <h2 class="section-title">RSVP & Ucapan</h2>
      <p class="section-subtitle">Konfirmasikan kehadiran Anda<br />dan berikan ucapan terbaik</p>
    </div>

    <!-- RSVP Form -->
    <div class="rsvp-form" data-aos="fade-up">
      <!-- Name Input -->
      <div class="form-group">
        <label class="form-label">Nama Tamu</label>
        <input
          v-model="guestName"
          type="text"
          class="form-input"
          placeholder="Masukkan nama Anda"
        />
      </div>

      <!-- Attendance Toggle -->
      <div class="form-group">
        <label class="form-label">Kehadiran</label>
        <div class="attendance-toggle">
          <button
            class="toggle-btn"
            :class="{ active: attendance === 'hadir' }"
            @click="attendance = 'hadir'"
          >
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
              <path d="M20 6L9 17L4 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
            Berdiri Hadir
          </button>
          <button
            class="toggle-btn"
            :class="{ active: attendance === 'tidak' }"
            @click="attendance = 'tidak'"
          >
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
              <path d="M18 6L6 18M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
            Tidak Hadir
          </button>
        </div>
      </div>

      <!-- Guest Count -->
      <div class="form-group">
        <label class="form-label">Jumlah Tamu</label>
        <div class="guest-count">
          <button
            class="count-btn"
            @click="guestCount = Math.max(1, guestCount - 1)"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
            </svg>
          </button>
          <span class="count-num">{{ guestCount }}</span>
          <button
            class="count-btn"
            @click="guestCount = Math.min(3, guestCount + 1)"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M12 5V19M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
            </svg>
          </button>
        </div>
      </div>

      <!-- Message -->
      <div class="form-group">
        <label class="form-label">Ucapan & Doa</label>
        <textarea
          v-model="message"
          class="form-textarea"
          placeholder="Tulis ucapan dan doa terbaik Anda untuk kami..."
          rows="4"
        ></textarea>
      </div>

      <!-- Submit Button -->
      <button class="submit-btn" @click="sendToWhatsApp">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M22 2L11 13M22 2L15 22L11 13M22 2L2 9L11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        Kirim via WhatsApp
      </button>
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
.rsvp {
  padding: 60px 24px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.8s ease;
}

.rsvp.visible {
  opacity: 1;
  transform: translateY(0);
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

/* RSVP Form */
.rsvp-form {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-label {
  font-family: 'Lato', sans-serif;
  font-size: clamp(11px, 2.5vw, 13px);
  color: #8a8070;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.form-input {
  padding: 12px 16px;
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 12px;
  font-family: 'Lato', sans-serif;
  font-size: 14px;
  color: #2c2c2c;
  background: rgba(255, 255, 255, 0.9);
  transition: all 0.3s ease;
}

.form-input:focus {
  outline: none;
  border-color: #d4b483;
  box-shadow: 0 0 0 3px rgba(212, 180, 131, 0.15);
}

.form-input::placeholder {
  color: #c0b8a8;
}

.form-textarea {
  padding: 12px 16px;
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 12px;
  font-family: 'Lato', sans-serif;
  font-size: 14px;
  color: #2c2c2c;
  background: rgba(255, 255, 255, 0.9);
  resize: vertical;
  transition: all 0.3s ease;
}

.form-textarea:focus {
  outline: none;
  border-color: #d4b483;
  box-shadow: 0 0 0 3px rgba(212, 180, 131, 0.15);
}

.form-textarea::placeholder {
  color: #c0b8a8;
}

/* Attendance Toggle */
.attendance-toggle {
  display: flex;
  gap: 12px;
}

.toggle-btn {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px 16px;
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.9);
  color: #8a8070;
  font-family: 'Lato', sans-serif;
  font-size: 13px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.toggle-btn:hover {
  border-color: #d4b483;
  color: #d4b483;
}

.toggle-btn.active {
  background: linear-gradient(135deg, rgba(212, 180, 131, 0.2), rgba(212, 180, 131, 0.1));
  border-color: #d4b483;
  color: #d4b483;
}

/* Guest Count */
.guest-count {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  padding: 8px;
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid rgba(212, 180, 131, 0.3);
  border-radius: 12px;
}

.count-btn {
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(212, 180, 131, 0.4);
  border-radius: 50%;
  background: transparent;
  color: #d4b483;
  cursor: pointer;
  transition: all 0.3s ease;
}

.count-btn:hover {
  background: rgba(212, 180, 131, 0.15);
}

.count-num {
  font-family: 'Playfair Display', serif;
  font-size: 24px;
  color: #d4b483;
  font-weight: 500;
  min-width: 30px;
  text-align: center;
}

/* Submit Button */
.submit-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  padding: 16px 24px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(135deg, #d4b483, #c8a870);
  color: white;
  font-family: 'Lato', sans-serif;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 6px 20px rgba(212, 180, 131, 0.35);
  margin-top: 8px;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 28px rgba(212, 180, 131, 0.45);
}

.submit-btn:active {
  transform: translateY(0);
}

/* Bottom Decoration */
.bottom-decoration {
  position: relative;
  z-index: 2;
  margin-top: 50px;
}

/* Responsive */
@media (max-width: 360px) {
  .rsvp {
    padding: 50px 16px;
  }

  .attendance-toggle {
    flex-direction: column;
  }
}
</style>
