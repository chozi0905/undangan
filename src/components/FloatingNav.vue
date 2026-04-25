<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const navItems = [
  { id: 'hero', label: 'Home', icon: 'home' },
  { id: 'mempelai', label: 'Mempelai', icon: 'user' },
  { id: 'event', label: 'Event', icon: 'calendar' },
  { id: 'story', label: 'Cerita', icon: 'heart' },
  { id: 'gallery', label: 'Gallery', icon: 'image' },
  { id: 'rsvp', label: 'RSVP', icon: 'message' },
  { id: 'gift', label: 'Hadiah', icon: 'gift' }
]

const scrollToSection = (id) => {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
    isOpen.value = false
  }
}
</script>

<template>
  <div class="floating-nav">
    <!-- Toggle Button -->
    <button class="toggle-btn" @click="isOpen = !isOpen" :class="{ active: isOpen }">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
        <path v-if="!isOpen" d="M3 12H21M3 6H21M3 18H21" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
        <path v-else d="M6 18L18 6M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      </svg>
    </button>

    <!-- Navigation Menu -->
    <transition name="fade">
      <div v-if="isOpen" class="nav-menu">
        <button
          v-for="item in navItems"
          :key="item.id"
          class="nav-item"
          @click="scrollToSection(item.id)"
          :title="item.label"
        >
          <!-- Home Icon -->
          <svg v-if="item.icon === 'home'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M3 9L12 2L21 9V20C21 20.5304 20.7893 21.0391 20.4142 21.4142C20.0391 21.7893 19.5304 22 19 22H5C4.46957 22 3.96086 21.7893 3.58579 21.4142C3.21071 21.0391 3 20.5304 3 20V9Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M9 22V12H15V22" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <!-- User Icon -->
          <svg v-else-if="item.icon === 'user'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M20 21V19C20 17.9391 19.5786 16.9217 18.8284 16.1716C18.0783 15.4214 17.0609 15 16 15H8C6.93913 15 5.92172 15.4214 5.17157 16.1716C4.42143 16.9217 4 17.9391 4 19V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <circle cx="12" cy="7" r="4" stroke="currentColor" stroke-width="2"/>
          </svg>
          <!-- Calendar Icon -->
          <svg v-else-if="item.icon === 'calendar'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <rect x="3" y="4" width="18" height="18" rx="2" stroke="currentColor" stroke-width="2"/>
            <path d="M16 2V6M8 2V6M3 10H21" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
          <!-- Heart Icon -->
          <svg v-else-if="item.icon === 'heart'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <!-- Image/Grid Icon -->
          <svg v-else-if="item.icon === 'image'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <rect x="3" y="3" width="18" height="18" rx="2" stroke="currentColor" stroke-width="2"/>
            <circle cx="8.5" cy="8.5" r="1.5" fill="currentColor"/>
            <path d="M21 15L16 10L5 21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <!-- Message/Edit Icon -->
          <svg v-else-if="item.icon === 'message'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M21 11.5C21 16.1944 16.5228 20 11.5 20C9.36227 20 7.49378 19.4746 5.95901 18.5627C4.73173 17.8446 3.73173 16.8446 3.01361 15.6174C2.10168 14.0826 1.57629 12.2141 1.57629 10.0764C1.57629 5.27985 5.77957 1.07658 10.5763 1.07658H11.5763C16.373 1.07658 20.5763 5.27985 20.5763 10.0766C20.5763 10.6628 20.5036 11.0936 20.435 11.5" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
            <path d="M8 9H16M8 13H13" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
          <!-- Gift Icon -->
          <svg v-else-if="item.icon === 'gift'" width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M20 12V22H4V12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M22 12H2V9C2 7.89543 2.89543 7 4 7H8C9.10457 7 10 7.89543 10 9" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M6 12V22" stroke="currentColor" stroke-width="2"/>
            <path d="M18 12V22" stroke="currentColor" stroke-width="2"/>
            <path d="M12 12V22" stroke="currentColor" stroke-width="2"/>
          </svg>
        </button>
      </div>
    </transition>
  </div>
</template>

<style scoped>
.floating-nav {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1000;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.toggle-btn {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: linear-gradient(135deg, #d4b483, #c4a070);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(212, 180, 131, 0.4);
  color: white;
  transition: all 0.3s ease;
}

.toggle-btn:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(212, 180, 131, 0.5);
}

.toggle-btn.active {
  background: linear-gradient(135deg, #b8976a, #a08658);
  transform: rotate(90deg);
}

.nav-menu {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 280px;
  padding: 12px;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 25px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
}

.nav-item {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: linear-gradient(135deg, #f8f4ef, #fff);
  border: 2px solid #d4b483;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #d4b483;
  transition: all 0.3s ease;
}

.nav-item:hover {
  background: linear-gradient(135deg, #d4b483, #c4a070);
  color: white;
  transform: scale(1.1);
}

/* Transition */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>