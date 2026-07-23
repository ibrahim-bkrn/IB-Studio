<template>
  <div class="app">
    <div class="dots-field" aria-hidden="true"></div>
    <NavBar />
    <main>
      <HeroSection id="hero" />
      <div class="hero-services-orb" aria-hidden="true"></div>
      <ServicesSection id="services" />
      <PortfolioSection id="portfolio" />
      <DifferentialSection id="pourquoi" />
      <AboutSection id="apropos" />
      <div class="about-process-orb" aria-hidden="true"></div>
      <ProcessSection id="processus" />
      <div class="process-faq-orb" aria-hidden="true"></div>
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

.dots-field {
  position: fixed;
  inset: 0;
  z-index: 999;
  pointer-events: none;
}

.dots-field::before,
.dots-field::after {
  content: '';
  position: absolute;
  inset: 0;
  background-size: 700px 700px;
  animation: dots-drift 18s ease-in-out infinite alternate,
             star-twinkle 4s ease-in-out infinite;
}

.dots-field::before {
  background-image:
    radial-gradient(2px 2px at 10% 15%, rgba(96, 165, 250, 0.6), transparent 60%),
    radial-gradient(1.5px 1.5px at 30% 70%, rgba(96, 165, 250, 0.5), transparent 60%),
    radial-gradient(2px 2px at 55% 25%, rgba(37, 99, 235, 0.5), transparent 60%),
    radial-gradient(1.5px 1.5px at 75% 55%, rgba(96, 165, 250, 0.45), transparent 60%),
    radial-gradient(2px 2px at 90% 85%, rgba(37, 99, 235, 0.5), transparent 60%);
}

.dots-field::after {
  background-image:
    radial-gradient(1.5px 1.5px at 20% 90%, rgba(96, 165, 250, 0.4), transparent 60%),
    radial-gradient(2px 2px at 45% 45%, rgba(96, 165, 250, 0.5), transparent 60%),
    radial-gradient(1.5px 1.5px at 65% 10%, rgba(37, 99, 235, 0.45), transparent 60%),
    radial-gradient(2px 2px at 85% 35%, rgba(96, 165, 250, 0.5), transparent 60%),
    radial-gradient(1.5px 1.5px at 5% 55%, rgba(37, 99, 235, 0.4), transparent 60%);
  animation-duration: 18s, 6s;
  animation-delay: 0s, -2s;
}

@keyframes dots-drift {
  0%   { background-position: 0px 0px; }
  50%  { background-position: 12px 18px; }
  100% { background-position: -10px 8px; }
}

@keyframes star-twinkle {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}

.hero-services-orb {
  position: relative;
  height: 0;
  z-index: 1;
}

.hero-services-orb::before {
  content: '';
  position: absolute;
  bottom: -60px;
  right: -120px;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(96, 165, 250, 0.25) 0%, rgba(37, 99, 235, 0.08) 50%, transparent 70%);
  filter: blur(80px);
  pointer-events: none;
  animation: orb-float 11s ease-in-out infinite reverse;
}

@keyframes orb-float {
  0%, 100% { transform: translateY(0px) scale(1); }
  50% { transform: translateY(-30px) scale(1.05); }
}

.about-process-orb,
.process-faq-orb {
  position: relative;
  height: 0;
  z-index: 1;
}

.about-process-orb::before {
  content: '';
  position: absolute;
  bottom: -50px;
  left: -150px;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.18) 0%, transparent 70%);
  filter: blur(100px);
  pointer-events: none;
}

.process-faq-orb::before {
  content: '';
  position: absolute;
  bottom: -60px;
  right: -100px;
  width: 400px;
  height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(96, 165, 250, 0.12) 0%, transparent 70%);
  filter: blur(100px);
  pointer-events: none;
}

</style>
