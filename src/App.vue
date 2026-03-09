<template>
  <div class="app" @mousemove="onMouseMove">
    <LoaderScreen />
    <div class="cursor" :style="cursorStyle" aria-hidden="true"></div>
    <NavBar />
    <main>
      <HeroSection id="hero" />
      <ServicesSection id="services" />
      <AboutSection id="apropos" />
      <ProcessSection id="processus" />
      <ProjectSection id="projet" />
      <FaqSection id="faq" />
      <ContactSection id="contact" />
    </main>
    <FooterSection />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import LoaderScreen from './components/LoaderScreen.vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ProcessSection from './components/ProcessSection.vue'
import ProjectSection from './components/ProjectSection.vue'
import FaqSection from './components/FaqSection.vue'
import ContactSection from './components/ContactSection.vue'
import AboutSection from './components/AboutSection.vue'
import FooterSection from './components/FooterSection.vue'

const mouseX = ref(-100)
const mouseY = ref(-100)

function onMouseMove(e) {
  mouseX.value = e.clientX
  mouseY.value = e.clientY
}

const cursorStyle = computed(() => ({
  transform: `translate(${mouseX.value - 10}px, ${mouseY.value - 10}px)`,
}))
</script>

<style scoped>
.app {
  position: relative;
}

.cursor {
  position: fixed;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: rgba(37, 99, 235, 0.5);
  pointer-events: none;
  z-index: 9999;
  transition: transform 0.1s ease;
  mix-blend-mode: screen;
}

@media (hover: none) {
  .cursor {
    display: none;
  }
}
</style>
