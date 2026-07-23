<template>
  <section class="stats" aria-label="Chiffres clés">
    <div class="stats-container" ref="el">
      <div
        v-for="(stat, i) in stats"
        :key="i"
        class="stat-card"
        :class="{ visible: isVisible }"
        :style="{ transitionDelay: `${i * 0.12}s` }"
      >
        <div class="stat-value">
          <span class="stat-number">{{ isVisible ? displayed[i] : 0 }}</span>
          <span class="stat-suffix">{{ stat.suffix }}</span>
        </div>
        <div class="stat-label">{{ stat.label }}</div>
        <div class="stat-bar">
          <div
            class="stat-bar-fill"
            :style="{ width: isVisible ? '100%' : '0%', transitionDelay: `${i * 0.12 + 0.3}s` }"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, watch } from 'vue'
import { useIntersection } from '../composables/useIntersection.js'

const { el, isVisible } = useIntersection({ threshold: 0.3 })

const stats = [
  { target: 12, suffix: '+', label: 'Projets livrés' },
  { target: 100, suffix: '%', label: 'Satisfaction client' },
  { target: 24, suffix: 'h', label: 'Délai de réponse' },
]

const displayed = ref([0, 0, 0])

function animateCount(index, target, duration = 1400) {
  const start = performance.now()
  function step(now) {
    const progress = Math.min((now - start) / duration, 1)
    const eased = 1 - Math.pow(1 - progress, 3)
    displayed.value[index] = Math.round(eased * target)
    if (progress < 1) requestAnimationFrame(step)
  }
  requestAnimationFrame(step)
}

watch(isVisible, (v) => {
  if (v) {
    stats.forEach((s, i) => {
      setTimeout(() => animateCount(i, s.target), i * 120)
    })
  }
})
</script>

<style scoped>
.stats {
  background: #0A0F1E;
  padding: 80px 24px;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.stats-container {
  max-width: 900px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
}

.stat-card {
  padding: 40px 48px;
  opacity: 0;
  transform: translateY(44px);
  transition: opacity 0.85s cubic-bezier(0.16, 1, 0.3, 1), transform 0.85s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
}

.stat-card:not(:last-child)::after {
  content: '';
  position: absolute;
  right: 0;
  top: 20%;
  height: 60%;
  width: 1px;
  background: rgba(255, 255, 255, 0.08);
}

.stat-card.visible {
  opacity: 1;
  transform: translateY(0);
}

.stat-value {
  display: flex;
  align-items: baseline;
  gap: 2px;
  margin-bottom: 10px;
}

.stat-number {
  font-size: 56px;
  font-weight: 800;
  letter-spacing: -3px;
  background: linear-gradient(135deg, #fff 0%, #60A5FA 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
}

.stat-suffix {
  font-size: 28px;
  font-weight: 700;
  color: #2563EB;
  letter-spacing: -1px;
}

.stat-label {
  font-size: 14px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.45);
  letter-spacing: 0.3px;
  margin-bottom: 20px;
}

.stat-bar {
  height: 2px;
  background: rgba(255, 255, 255, 0.06);
  border-radius: 2px;
  overflow: hidden;
}

.stat-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 2px;
  transition: width 1s cubic-bezier(0.4, 0, 0.2, 1);
  width: 0%;
}

@media (max-width: 768px) {
  .stats-container {
    grid-template-columns: 1fr;
    gap: 0;
  }

  .stat-card {
    padding: 32px 24px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  }

  .stat-card:not(:last-child)::after {
    display: none;
  }

  .stat-number {
    font-size: 44px;
  }
}
</style>
