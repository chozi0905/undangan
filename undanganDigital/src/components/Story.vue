<script setup>
import bgStory from '@/assets/picture/backgroundStory.png'

// Story timeline data
const stories = [
  {
    id: 1,
    title: 'Pertemuan Pertama',
    date: 'Oktober 2017',
    description: 'Semuanya bermula dari sebuah pertemuan yang sederhana. Dua orang yang tidak disangka ternyata memiliki banyak kesamaan. Satu kali pertemuan yang tidak disangka membawa cerita yang begitu indah.',
    icon: 'heart'
  },
  {
    id: 2,
    title: 'Menjalin Kedekatan',
    date: 'Desember 2018',
    description: 'Seiring waktu, kami belajar saling menghargai dan memahami. Setiap hari bersama terasa begitu bermakna. Kedekatan yang tumbuh perlahan tapi pasti membawa kami lebih dekat.',
    icon: 'flower'
  },
  {
    id: 3,
    title: 'Ijab Kabul',
    date: 'Desember 2026',
    description: 'Akhirnya menjadi hari yang kami tunggu. Dengan restu keluarga dan teman-teman tercinta, kami resmi melangkah bersama dalam satu ikatan yang sakral.',
    icon: 'ring'
  }
]
</script>

<template>
  <section class="story" :style="{ backgroundImage: `url(${bgStory})` }">
    <div class="overlay"></div>

    <!-- Section Header -->
    <div class="section-header">
      <div class="header-ornament">
        <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
          <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>
          <path d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z" fill="#d4b483"/>
        </svg>
      </div>
      <h2 class="section-title">Our Love Story</h2>
      <p class="section-subtitle">Kisah cinta yang membawa kami hingga di sini</p>
    </div>

    <!-- Timeline -->
    <div class="timeline">
      <div class="timeline-line"></div>

      <div
        v-for="(item, index) in stories"
        :key="item.id"
        class="timeline-item"
        :class="{ 'timeline-right': index % 2 !== 0 }"
        data-aos="fade-up"
      >
        <!-- Icon -->
        <div class="timeline-icon">
          <!-- Heart Icon -->
          <svg v-if="item.icon === 'heart'" width="28" height="28" viewBox="0 0 28 28" fill="none">
            <path d="M14 24 C14 24, 4 17, 4 10 C4 6, 7.5 3, 11 3 C12.5 3, 14 4, 14 4 C14 4, 15.5 3, 17 3 C20.5 3, 24 6, 24 10 C24 17, 14 24, 14 24Z" fill="#d4b483"/>
          </svg>
          <!-- Flower Icon -->
          <svg v-if="item.icon === 'flower'" width="28" height="28" viewBox="0 0 28 28" fill="none">
            <circle cx="14" cy="14" r="4" fill="#d4b483"/>
            <ellipse cx="14" cy="6" rx="3" ry="5" fill="#f0d78c" opacity="0.8"/>
            <ellipse cx="14" cy="22" rx="3" ry="5" fill="#f0d78c" opacity="0.8"/>
            <ellipse cx="6" cy="14" rx="5" ry="3" fill="#f0d78c" opacity="0.8"/>
            <ellipse cx="22" cy="14" rx="5" ry="3" fill="#f0d78c" opacity="0.8"/>
          </svg>
          <!-- Ring Icon -->
          <svg v-if="item.icon === 'ring'" width="28" height="28" viewBox="0 0 28 28" fill="none">
            <circle cx="14" cy="16" r="8" stroke="#d4b483" stroke-width="2" fill="none"/>
            <path d="M14 8 C14 8, 11 5, 9 8 C7 11, 10 14, 14 12" fill="#d4b483"/>
          </svg>
        </div>

        <!-- Card -->
        <div class="timeline-card">
          <span class="timeline-date">{{ item.date }}</span>
          <h3 class="timeline-title">{{ item.title }}</h3>
          <p class="timeline-description">{{ item.description }}</p>
        </div>
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
.story {
  padding: 60px 24px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.3) 0%,
    rgba(255, 255, 255, 0.6) 30%,
    rgba(255, 255, 255, 0.85) 70%,
    rgba(255, 255, 255, 0.95) 100%
  );
  z-index: 1;
}

/* Section Header */
.section-header {
  position: relative;
  z-index: 2;
  text-align: center;
  margin-bottom: 50px;
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

/* Timeline */
.timeline {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 500px;
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.timeline-line {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: linear-gradient(to bottom, transparent, #d4b483 10%, #d4b483 90%, transparent);
}

.timeline-item {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  position: relative;
}

.timeline-right {
  flex-direction: row-reverse;
}

.timeline-icon {
  width: 56px;
  height: 56px;
  min-width: 56px;
  background: white;
  border: 2px solid #d4b483;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 2;
}

.timeline-card {
  flex: 1;
  background: rgba(255, 255, 255, 0.9);
  border: 1px solid rgba(212, 180, 131, 0.25);
  border-radius: 16px;
  padding: 20px;
  text-align: left;
}

.timeline-date {
  font-family: 'Lato', sans-serif;
  font-size: 11px;
  color: #d4b483;
  letter-spacing: 2px;
  text-transform: uppercase;
}

.timeline-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(16px, 4vw, 20px);
  color: #2c2c2c;
  font-weight: 500;
  margin: 6px 0 10px;
}

.timeline-description {
  font-family: 'Lato', sans-serif;
  font-size: clamp(12px, 3vw, 14px);
  color: #6a6050;
  line-height: 1.7;
}

/* Bottom Decoration */
.bottom-decoration {
  position: relative;
  z-index: 2;
  margin-top: 50px;
}

/* Responsive */
@media (max-width: 600px) {
  .timeline-line {
    left: 28px;
  }

  .timeline-right {
    flex-direction: row;
  }

  .timeline-item {
    padding-left: 60px;
  }

  .timeline-icon {
    position: absolute;
    left: 0;
  }

  .timeline-card {
    text-align: center;
  }
}

@media (max-width: 360px) {
  .story {
    padding: 50px 16px;
  }

  .timeline {
    gap: 30px;
  }
}
</style>
