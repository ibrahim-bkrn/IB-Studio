<template>
  <div class="app">
    <NavBar />
    <main>
      <HeroSection id="hero" />
      <ServicesSection id="services" />
      <PortfolioSection id="portfolio" />
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
</script>

<style scoped>
.app {
  position: relative;
  width: 100%;
  overflow-x: clip;
}
</style>
