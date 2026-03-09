<template>
  <section class="stack" aria-label="Technologies maîtrisées">
    <div class="stack-header" ref="el" :class="{ visible: isVisible }">
      <p class="stack-label">Stack technique</p>
      <p class="stack-sub">Des outils choisis pour leur performance, pas pour suivre les tendances.</p>
    </div>

    <div class="marquee-wrapper" aria-hidden="true">
      <div class="marquee-fade-left"></div>
      <div class="marquee-fade-right"></div>

      <!-- Ligne 1 — gauche vers droite -->
      <div class="marquee-track track-1">
        <div class="marquee-inner">
          <span v-for="tech in [...techs, ...techs]" :key="tech.name + Math.random()" class="tech-pill">
            <span class="tech-dot" :style="{ background: tech.color }"></span>
            {{ tech.name }}
          </span>
        </div>
      </div>

      <!-- Ligne 2 — droite vers gauche -->
      <div class="marquee-track track-2">
        <div class="marquee-inner reverse">
          <span v-for="tech in [...techsAlt, ...techsAlt]" :key="tech.name + Math.random()" class="tech-pill">
            <span class="tech-dot" :style="{ background: tech.color }"></span>
            {{ tech.name }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'
const { el, isVisible } = useIntersection()

const techs = [
  { name: 'Vue.js',      color: '#42b883' },
  { name: 'React',       color: '#61DAFB' },
  { name: 'JavaScript',  color: '#F7DF1E' },
  { name: 'TypeScript',  color: '#3178C6' },
  { name: 'Node.js',     color: '#68A063' },
  { name: 'Tailwind CSS',color: '#38BDF8' },
  { name: 'Figma',       color: '#F24E1E' },
  { name: 'WordPress',   color: '#21759B' },
]

const techsAlt = [
  { name: 'HTML5',       color: '#E34F26' },
  { name: 'CSS3',        color: '#1572B6' },
  { name: 'Vite',        color: '#646CFF' },
  { name: 'Git',         color: '#F05032' },
  { name: 'SEO',         color: '#10B981' },
  { name: 'MySQL',       color: '#4479A1' },
  { name: 'REST API',    color: '#60A5FA' },
  { name: 'Webflow',     color: '#4353FF' },
]
</script>

<style scoped>
.stack {
  background: #F8FAFC;
  padding: 80px 0 72px;
  overflow: hidden;
}

.stack-header {
  max-width: 1100px;
  margin: 0 auto 48px;
  padding: 0 24px;
  opacity: 0;
  transform: translateY(16px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.stack-header.visible {
  opacity: 1;
  transform: translateY(0);
}

.stack-label {
  font-size: 11px;
  font-weight: 700;
  color: #2563EB;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 10px;
}

.stack-sub {
  font-size: 15px;
  color: #94A3B8;
  font-weight: 400;
}

/* ── Marquee ── */
.marquee-wrapper {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.marquee-fade-left,
.marquee-fade-right {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 120px;
  z-index: 2;
  pointer-events: none;
}

.marquee-fade-left {
  left: 0;
  background: linear-gradient(90deg, #F8FAFC, transparent);
}

.marquee-fade-right {
  right: 0;
  background: linear-gradient(-90deg, #F8FAFC, transparent);
}

.marquee-track {
  overflow: hidden;
}

.marquee-inner {
  display: flex;
  gap: 12px;
  width: max-content;
  animation: marquee-left 28s linear infinite;
}

.marquee-inner.reverse {
  animation: marquee-right 32s linear infinite;
}

@keyframes marquee-left {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

@keyframes marquee-right {
  from { transform: translateX(-50%); }
  to   { transform: translateX(0); }
}

.tech-pill {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  background: #fff;
  border: 1px solid #E2E8F0;
  border-radius: 50px;
  font-size: 14px;
  font-weight: 600;
  color: #1E293B;
  white-space: nowrap;
  box-shadow: 0 1px 3px rgba(0,0,0,0.04);
  transition: border-color 0.2s ease;
  flex-shrink: 0;
}

.tech-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  flex-shrink: 0;
}
</style>
