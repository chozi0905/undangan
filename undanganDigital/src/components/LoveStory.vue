<script setup>
import { ref, onMounted } from 'vue'

const stories = ref([
  {
    id: 1,
    title: 'Pertemuan Pertama',
    date: 'November 2019',
    description: 'Ini adalah awal dari semuanya, saat pertama kali kami bertemu dan berbagi cerita.',
    icon: 'heart'
  },
  {
    id: 2,
    title: 'Menjalin Kedekatan',
    date: 'Desember 2020',
    description: 'Seiring waktu, kami semakin mengenal satu sama lain dan menemukan kedekatan yang indah.',
    icon: 'flower'
  },
  {
    id: 3,
    title: 'Ijab Kabul',
    date: '20 Desember 2026',
    description: 'Dengan segala cintanya, kami memutuskan untuk melangkah bersama dalam hidup.',
    icon: 'ring'
  }
])

const visibleItems = ref([])

onMounted(() => {
  stories.value.forEach((_, index) => {
    setTimeout(() => {
      visibleItems.value.push(index)
    }, index * 200)
  })
})
</script>

<template>
  <section class="love-story">
    <!-- Background Decorations -->
    <div class="bg-decoration">
      <svg class="deco-flower deco-1" width="40" height="40" viewBox="0 0 40 40" fill="none">
        <circle cx="20" cy="20" r="5" fill="#f8b4c4"/>
        <ellipse cx="20" cy="8" rx="4" ry="6" fill="#f8b4c4" opacity="0.6"/>
        <ellipse cx="20" cy="32" rx="4" ry="6" fill="#f8b4c4" opacity="0.6"/>
        <ellipse cx="8" cy="20" rx="6" ry="4" fill="#f8b4c4" opacity="0.6"/>
        <ellipse cx="32" cy="20" rx="6" ry="4" fill="#f8b4c4" opacity="0.6"/>
      </svg>
      <svg class="deco-flower deco-2" width="30" height="30" viewBox="0 0 40 40" fill="none">
        <circle cx="20" cy="20" r="4" fill="#d4b483"/>
        <ellipse cx="20" cy="10" rx="3" ry="5" fill="#d4b483" opacity="0.5"/>
        <ellipse cx="20" cy="30" rx="3" ry="5" fill="#d4b483" opacity="0.5"/>
        <ellipse cx="10" cy="20" rx="5" ry="3" fill="#d4b483" opacity="0.5"/>
        <ellipse cx="30" cy="20" rx="5" ry="3" fill="#d4b483" opacity="0.5"/>
      </svg>
      <svg class="deco-star deco-3" width="24" height="24" viewBox="0 0 24 24" fill="none">
        <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483" opacity="0.4"/>
      </svg>
      <svg class="deco-star deco-4" width="20" height="20" viewBox="0 0 24 24" fill="none">
        <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#f8b4c4" opacity="0.5"/>
      </svg>
    </div>

    <!-- Section Header -->
    <div class="section-header" data-aos="fade-down">
      <div class="header-ornament">
        <svg width="40" height="20" viewBox="0 0 40 20" fill="none">
          <path d="M0 10 L15 10 M25 10 L40 10" stroke="#d4b483" stroke-width="1"/>
          <path d="M20 1 L21 9 L29 10 L21 11 L20 19 L19 11 L11 10 L19 9 Z" fill="#d4b483"/>
        </svg>
      </div>
      <h2 class="section-title">Our Love Story</h2>
      <p class="section-subtitle">Kisah cinta kami yang indah</p>
    </div>

    <!-- Story Timeline -->
    <div class="timeline">
      <div
        v-for="(story, index) in stories"
        :key="story.id"
        class="timeline-item"
        :class="{
          'visible': visibleItems.includes(index),
          'left': index % 2 === 0,
          'right': index % 2 !== 0
        }"
      >
        <!-- Timeline Line -->
        <div class="timeline-line"></div>

        <!-- Timeline Dot -->
        <div class="timeline-dot">
          <svg v-if="story.icon === 'heart'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z" fill="#d4b483"/>
          </svg>
          <svg v-if="story.icon === 'flower'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="12" r="4" fill="#d4b483"/>
            <ellipse cx="12" cy="4" rx="3" ry="4" fill="#f8b4c4"/>
            <ellipse cx="12" cy="20" rx="3" ry="4" fill="#f8b4c4"/>
            <ellipse cx="4" cy="12" rx="4" ry="3" fill="#f8b4c4"/>
            <ellipse cx="20" cy="12" rx="4" ry="3" fill="#f8b4c4"/>
          </svg>
          <svg v-if="story.icon === 'ring'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="14" r="7" stroke="#d4b483" stroke-width="2" fill="none"/>
            <path d="M12 7 L12 3 M9 5 L12 3 L15 5" stroke="#d4b483" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </div>

        <!-- Story Card -->
        <div class="story-card" data-aos="fade-up">
          <div class="card-date">{{ story.date }}</div>
          <h3 class="card-title">{{ story.title }}</h3>
          <p class="card-description">{{ story.description }}</p>
          <div class="card-ornament">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M12 2 L13.5 10 L21 12 L13.5 13.5 L12 22 L10.5 13.5 L3 12 L10.5 10 Z" fill="#d4b483" opacity="0.5"/>
            </svg>
          </div>
        </div>
      </div>
    </div>

    <!-- Bottom Decoration -->
    <div class="bottom-decoration" data-aos="fade-up">
      <svg width="60" height="30" viewBox="0 0 60 30" fill="none">
        <path d="M0 15 L20 15 M40 15 L60 15" stroke="#d4b483" stroke-width="1"/>
        <path d="M30 5 L32 13 L40 15 L32 17 L30 25 L28 17 L20 15 L28 13 Z" fill="#d4b483"/>
      </svg>
    </div>
  </section>
</template>

<style scoped>
.love-story {
  padding: 80px 24px;
  background: linear-gradient(135deg, #fff5f5 0%, #fff9f5 50%, #fff5f9 100%);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Background Decorations */
.bg-decoration {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
}

.deco-flower,
.deco-star {
  position: absolute;
  animation: float 6s ease-in-out infinite;
}

.deco-1 { top: 10%; left: 5%; animation-delay: 0s; }
.deco-2 { top: 20%; right: 8%; animation-delay: 1s; }
.deco-3 { bottom: 15%; left: 10%; animation-delay: 2s; }
.deco-4 { bottom: 25%; right: 5%; animation-delay: 0.5s; }

@keyframes float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-10px) rotate(10deg); }
}

/* Section Header */
.section-header {
  text-align: center;
  margin-bottom: 60px;
  position: relative;
  z-index: 2;
}

.header-ornament {
  margin-bottom: 16px;
}

.section-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(28px, 6vw, 36px);
  color: #2c2c2c;
  font-weight: 500;
  margin-bottom: 8px;
}

.section-subtitle {
  font-family: 'Lato', sans-serif;
  font-size: clamp(14px, 3vw, 16px);
  color: #8a8070;
  letter-spacing: 1px;
}

/* Timeline */
.timeline {
  position: relative;
  width: 100%;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 40px;
  padding: 20px 0;
}

.timeline-item {
  display: flex;
  align-items: center;
  position: relative;
  opacity: 0;
  transform: translateX(-30px);
  transition: all 0.6s ease;
}

.timeline-item.right {
  transform: translateX(30px);
}

.timeline-item.visible {
  opacity: 1;
  transform: translateX(0);
}

.timeline-line {
  position: absolute;
  left: 50%;
  top: 0;
  bottom: -40px;
  width: 2px;
  background: linear-gradient(to bottom, #d4b483, #f8b4c4, transparent);
  transform: translateX(-50%);
}

.timeline-item:last-child .timeline-line {
  display: none;
}

.timeline-dot {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 44px;
  height: 44px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(212, 180, 131, 0.3);
  border: 2px solid #d4b483;
  z-index: 3;
}

.story-card {
  flex: 1;
  background: white;
  border-radius: 20px;
  padding: 24px;
  box-shadow: 0 10px 40px rgba(248, 180, 196, 0.2);
  border: 1px solid rgba(212, 180, 131, 0.2);
  transition: all 0.3s ease;
  max-width: calc(50% - 40px);
}

.story-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 50px rgba(248, 180, 196, 0.3);
}

.timeline-item.left .story-card {
  margin-right: auto;
  text-align: right;
}

.timeline-item.right .story-card {
  margin-left: auto;
  text-align: left;
}

.card-date {
  font-family: 'Lato', sans-serif;
  font-size: 12px;
  color: #d4b483;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 8px;
}

.card-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(18px, 4vw, 22px);
  color: #2c2c2c;
  font-weight: 500;
  margin-bottom: 12px;
}

.card-description {
  font-family: 'Lato', sans-serif;
  font-size: clamp(13px, 3vw, 14px);
  color: #6a6a6a;
  line-height: 1.6;
}

.card-ornament {
  margin-top: 16px;
}

.timeline-item.left .card-ornament {
  display: flex;
  justify-content: flex-end;
}

.timeline-item.right .card-ornament {
  display: flex;
  justify-content: flex-start;
}

/* Bottom Decoration */
.bottom-decoration {
  margin-top: 60px;
  position: relative;
  z-index: 2;
}

/* Responsive */
@media (max-width: 600px) {
  .timeline-item {
    flex-direction: column;
    transform: translateX(0);
  }

  .timeline-item.right {
    transform: translateX(0);
  }

  .timeline-item.visible {
    transform: translateX(0);
  }

  .timeline-line {
    display: none;
  }

  .timeline-dot {
    position: static;
    transform: none;
    margin-bottom: 16px;
  }

  .story-card {
    max-width: 100%;
    text-align: left !important;
  }

  .timeline-item.left .card-ornament,
  .timeline-item.right .card-ornament {
    justify-content: flex-start;
  }
}
</style>
