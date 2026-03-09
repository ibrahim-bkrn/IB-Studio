<template>
  <Transition name="loader-fade">
    <div v-if="visible" class="loader" aria-hidden="true">
      <div class="loader-inner">
        <div class="loader-mark">
          <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="48" height="48" rx="12" fill="#2563EB"/>
            <text x="50%" y="56%" dominant-baseline="middle" text-anchor="middle"
              font-family="Inter,-apple-system,sans-serif"
              font-weight="800" font-size="20" fill="white" letter-spacing="-0.5">IB</text>
          </svg>
        </div>
        <div class="loader-bar">
          <div class="loader-progress"></div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const visible = ref(true)

onMounted(() => {
  setTimeout(() => {
    visible.value = false
  }, 1600)
})
</script>

<style scoped>
.loader {
  position: fixed;
  inset: 0;
  z-index: 99999;
  background: #0A0F1E;
  display: flex;
  align-items: center;
  justify-content: center;
}

.loader-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 28px;
}

.loader-mark {
  animation: mark-in 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
  opacity: 0;
}

@keyframes mark-in {
  from { opacity: 0; transform: scale(0.6); }
  to   { opacity: 1; transform: scale(1); }
}

.loader-bar {
  width: 120px;
  height: 2px;
  background: rgba(255, 255, 255, 0.08);
  border-radius: 2px;
  overflow: hidden;
}

.loader-progress {
  height: 100%;
  width: 0%;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 2px;
  animation: progress-fill 1.3s cubic-bezier(0.4, 0, 0.2, 1) 0.2s forwards;
}

@keyframes progress-fill {
  from { width: 0%; }
  to   { width: 100%; }
}

/* Sortie */
.loader-fade-leave-active {
  transition: opacity 0.4s ease, transform 0.4s ease;
}
.loader-fade-leave-to {
  opacity: 0;
  transform: scale(1.04);
}
</style>
