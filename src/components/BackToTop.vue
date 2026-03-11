<template>
  <Transition name="btt">
    <button
      v-if="visible"
      class="btt"
      @click="scrollTop"
      aria-label="Retour en haut"
    >
      <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M9 14V4M9 4L4 9M9 4L14 9" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </button>
  </Transition>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const visible = ref(false)

function onScroll() {
  visible.value = window.scrollY > 400
}

function scrollTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.btt {
  position: fixed;
  bottom: 32px;
  right: 32px;
  z-index: 200;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: #2563EB;
  color: #fff;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(37, 99, 235, 0.4);
  transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
}

.btt:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 28px rgba(37, 99, 235, 0.55);
  background: #1d4ed8;
}

.btt:active {
  transform: scale(0.93);
  transition-duration: 80ms;
}

.btt-enter-active,
.btt-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.btt-enter-from,
.btt-leave-to {
  opacity: 0;
  transform: translateY(12px);
}

@media (max-width: 768px) {
  .btt {
    bottom: 20px;
    right: 20px;
    width: 40px;
    height: 40px;
  }
}
</style>
