<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps(['autoplay'])
const isPlaying = ref(false)
const autoplayBlocked = ref(false)
const audio = ref(null)

const musicUrl = '/wedding-song.mp3'

const toggleMusic = () => {
  if (!audio.value) return

  if (isPlaying.value) {
    audio.value.pause()
  } else {
    audio.value.play()
  }
  isPlaying.value = !isPlaying.value
}

onMounted(() => {
  audio.value = new Audio(musicUrl)
  audio.value.loop = true

  // Auto play kalau autoplay = true
  if (props.autoplay) {
    audio.value.play().then(() => {
      isPlaying.value = true
    }).catch(() => {
      // Browser blocked auto-play
      autoplayBlocked.value = true
      isPlaying.value = false
    })
  }
})
</script>

<template>
  <div class="music-player" :class="{ playing: isPlaying }">
    <audio ref="audio" loop>
      <source :src="musicUrl" type="audio/mpeg" />
    </audio>

    <button class="music-btn" @click="toggleMusic" :title="isPlaying ? 'Matikan Musik' : 'Putar Musik'">
      <!-- Music Note Icon -->
      <svg v-if="!isPlaying" width="20" height="20" viewBox="0 0 24 24" fill="none">
        <path d="M9 18V5L21 3V16" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        <circle cx="6" cy="18" r="3" stroke="currentColor" stroke-width="2"/>
        <circle cx="18" cy="16" r="3" stroke="currentColor" stroke-width="2"/>
      </svg>
      <!-- Pause Icon -->
      <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none">
        <rect x="6" y="4" width="4" height="16" rx="1" fill="currentColor"/>
        <rect x="14" y="4" width="4" height="16" rx="1" fill="currentColor"/>
      </svg>

      <!-- Music Wave Animation -->
      <div v-if="isPlaying" class="wave">
        <span class="wave-bar"></span>
        <span class="wave-bar"></span>
        <span class="wave-bar"></span>
        <span class="wave-bar"></span>
      </div>

      <!-- Autoplay blocked hint -->
      <div v-if="autoplayBlocked && !isPlaying" class="hint">
        <svg width="10" height="10" viewBox="0 0 24 24" fill="none">
          <path d="M12 6V12L16 14" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </div>
    </button>
  </div>
</template>

<style scoped>
.music-player {
  position: fixed;
  bottom: 24px;
  right: 24px;
  z-index: 1000;
}

.music-btn {
  width: 52px;
  height: 52px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  border: 2px solid rgba(212, 180, 131, 0.6);
  background: rgba(255, 255, 255, 0.95);
  color: #d4b483;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 16px rgba(212, 180, 131, 0.25);
  position: relative;
  overflow: hidden;
}

.music-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 24px rgba(212, 180, 131, 0.35);
  border-color: #d4b483;
}

.music-player.playing .music-btn {
  background: linear-gradient(135deg, #d4b483, #c8a870);
  color: white;
  border-color: #d4b483;
}

/* Hint dot when autoplay blocked */
.hint {
  position: absolute;
  top: -4px;
  right: -4px;
  width: 14px;
  height: 14px;
  background: #e74c3c;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Wave Animation */
.wave {
  position: absolute;
  bottom: 6px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: flex-end;
  gap: 2px;
  height: 12px;
}

.wave-bar {
  width: 3px;
  background: white;
  border-radius: 2px;
  animation: wave 0.8s ease-in-out infinite;
}

.wave-bar:nth-child(1) { animation-delay: 0s; height: 6px; }
.wave-bar:nth-child(2) { animation-delay: 0.15s; height: 10px; }
.wave-bar:nth-child(3) { animation-delay: 0.3s; height: 8px; }
.wave-bar:nth-child(4) { animation-delay: 0.45s; height: 12px; }

@keyframes wave {
  0%, 100% { transform: scaleY(0.5); }
  50% { transform: scaleY(1); }
}

/* Responsive */
@media (max-width: 360px) {
  .music-player {
    bottom: 16px;
    right: 16px;
  }

  .music-btn {
    width: 46px;
    height: 46px;
  }
}
</style>
