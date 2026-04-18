<template>
  <div class="app" @mousemove="onMouseMove">
    <!-- Cursor : dot + ring -->
    <div class="cursor-dot" :style="dotStyle" aria-hidden="true"></div>
    <div class="cursor-ring" :class="{ hovering: isHovering }" :style="ringStyle" aria-hidden="true"></div>

    <NavBar />
    <main>
      <HeroSection id="hero" />
      <ServicesSection id="services" />
      <!-- <PortfolioSection id="portfolio" /> -->
      <DifferentialSection id="pourquoi" />
      <AboutSection id="apropos" />
      <ProcessSection id="processus" />
      <FaqSection id="faq" />
      <ContactSection id="contact" />
    </main>
    <FooterSection />
    <BackToTop />
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import DifferentialSection from './components/DifferentialSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProcessSection from './components/ProcessSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import FaqSection from './components/FaqSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
import BackToTop from './components/BackToTop.vue'

// ── Cursor dot (suit exactement) ──
const mouseX = ref(-100)
const mouseY = ref(-100)

// ── Cursor ring (suit avec lag via lerp) ──
const ringX = ref(-100)
const ringY = ref(-100)
const isHovering = ref(false)
let rafId = null

function lerp(a, b, t) { return a + (b - a) * t }

function animate() {
  ringX.value = lerp(ringX.value, mouseX.value, 0.1)
  ringY.value = lerp(ringY.value, mouseY.value, 0.1)
  rafId = requestAnimationFrame(animate)
}

function onMouseMove(e) {
  mouseX.value = e.clientX
  mouseY.value = e.clientY
}

function onMouseOver(e) {
  isHovering.value = !!e.target.closest('a, button, [role="button"], input, select, textarea, label')
}

onMounted(() => {
  animate()
  window.addEventListener('mouseover', onMouseOver, { passive: true })
})
onUnmounted(() => {
  cancelAnimationFrame(rafId)
  window.removeEventListener('mouseover', onMouseOver)
})

const dotStyle = computed(() => ({
  transform: `translate(${mouseX.value - 3}px, ${mouseY.value - 3}px)`,
}))

const ringStyle = computed(() => ({
  transform: `translate(${ringX.value - 18}px, ${ringY.value - 18}px)`,
}))
</script>

<style scoped>
.app {
  position: relative;
  width: 100%;
  overflow-x: clip;
}

/* ── Dot — suit exactement ── */
.cursor-dot {
  position: fixed;
  top: 0;
  left: 0;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #2563EB;
  pointer-events: none;
  z-index: 9999;
  mix-blend-mode: screen;
}

/* ── Ring — suit avec lag ── */
.cursor-ring {
  position: fixed;
  top: 0;
  left: 0;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1.5px solid rgba(37, 99, 235, 0.5);
  pointer-events: none;
  z-index: 9998;
  transition: width 0.2s ease, height 0.2s ease, border-color 0.2s ease, background 0.2s ease;
  mix-blend-mode: screen;
}

.cursor-ring.hovering {
  width: 52px;
  height: 52px;
  border-color: rgba(96, 165, 250, 0.7);
  background: rgba(37, 99, 235, 0.06);
  margin-left: -8px;
  margin-top: -8px;
}

@media (hover: none) {
  .cursor-dot,
  .cursor-ring {
    display: none;
  }
}
</style>
