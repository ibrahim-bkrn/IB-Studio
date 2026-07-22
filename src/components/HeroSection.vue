<template>
  <section class="hero" aria-label="Introduction">
    <div class="hero-orb hero-orb--1" aria-hidden="true" :style="orbStyle(0.02, 0.015)"></div>
    <div class="hero-orb hero-orb--2" aria-hidden="true" :style="orbStyle(-0.018, -0.012)"></div>
    <div class="hero-orb hero-orb--3" aria-hidden="true" :style="orbStyle(0.01, 0.02)"></div>
    <div class="hero-grid" aria-hidden="true"></div>

    <div class="hero-container">
      <div class="hero-content" :class="{ visible: mounted }">
        <h1 class="hero-title">
          Je conçois des sites web <br class="desktop-br">qui travaillent pour vous, pas l'inverse.
        </h1>

        <p class="hero-subtitle">
          Laissez votre site bosser pour vous (pas l'inverse) : conçu pour plaire, construit pour durer, fait pour attirer les bons clients.
        </p>

        <div class="hero-actions">
          <a href="#contact" class="btn-primary" aria-label="Discuter de votre projet">
            Parlons de votre projet
          </a>
          <a href="#services" class="btn-secondary" aria-label="Voir les services proposés">
            Voir mes services
          </a>
        </div>

        <div class="hero-stats" aria-label="Chiffres clés">
          <div class="stat-card">
            <span class="stat-number">+5</span>
            <span class="stat-label">Projets livrés</span>
          </div>
          <div class="stat-card">
            <span class="stat-number">3 ans</span>
            <span class="stat-label">d'expérience</span>
          </div>
          <div class="stat-card">
            <span class="stat-number">100%</span>
            <span class="stat-label">des clients sont satisfaits</span>
          </div>
        </div>
      </div>
    </div>

    <!--<div class="hero-scroll-indicator" aria-hidden="true">
      <div class="scroll-pill">
        <div class="scroll-pill-dot"></div>
      </div>
    </div>-->
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const mounted = ref(false)

// Parallax orbes
const mouseX = ref(0)
const mouseY = ref(0)

function onMouseMove(e) {
  mouseX.value = e.clientX - window.innerWidth / 2
  mouseY.value = e.clientY - window.innerHeight / 2
}

function orbStyle(factorX, factorY) {
  return {
    transform: `translate(${mouseX.value * factorX}px, ${mouseY.value * factorY}px)`,
    transition: 'transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94)',
  }
}

onMounted(() => {
  requestAnimationFrame(() => {
    mounted.value = true
  })
  window.addEventListener('mousemove', onMouseMove, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('mousemove', onMouseMove)
})
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100dvh;
  background: #0A0F1E;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  padding: 120px 24px 80px;
}


/* Orbes lumineux */
.hero-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
}

.hero-orb--1 {
  width: 650px;
  height: 650px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.4) 0%, rgba(79, 70, 229, 0.1) 50%, transparent 70%);
  top: -160px;
  left: -180px;
  animation: orb-float 9s ease-in-out infinite;
}

.hero-orb--2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(96, 165, 250, 0.25) 0%, rgba(37, 99, 235, 0.08) 50%, transparent 70%);
  bottom: -60px;
  right: -120px;
  animation: orb-float 11s ease-in-out infinite reverse;
}

.hero-orb--3 {
  width: 380px;
  height: 380px;
  background: radial-gradient(circle, rgba(139, 92, 246, 0.2) 0%, rgba(37, 99, 235, 0.12) 40%, transparent 70%);
  top: 50%;
  left: 55%;
  transform: translate(-50%, -50%);
  animation: orb-pulse 7s ease-in-out infinite;
}

@keyframes orb-float {
  0%, 100% { transform: translateY(0px) scale(1); }
  50% { transform: translateY(-30px) scale(1.05); }
}

@keyframes orb-pulse {
  0%, 100% { opacity: 0.5; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 0.8; transform: translate(-50%, -50%) scale(1.1); }
}

/* Grille de fond */
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.05) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
  mask-image: radial-gradient(ellipse 80% 60% at 50% 35%, black 10%, transparent 70%);
  -webkit-mask-image: radial-gradient(ellipse 80% 60% at 50% 35%, black 10%, transparent 70%);
}

.hero-container {
  max-width: 900px;
  width: 100%;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  text-align: center;
}

/* Animations au chargement — entrée échelonnée */
.hero-content {
  /* les enfants s'animent indépendamment */
}

.hero-title,
.hero-subtitle,
.hero-actions,
.hero-stats {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.75s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.75s cubic-bezier(0.4, 0, 0.2, 1);
}

.hero-content.visible .hero-title    { opacity: 1; transform: translateY(0); transition-delay: 0.08s; }
.hero-content.visible .hero-subtitle { opacity: 1; transform: translateY(0); transition-delay: 0.26s; }
.hero-content.visible .hero-actions  { opacity: 1; transform: translateY(0); transition-delay: 0.44s; }
.hero-content.visible .hero-stats    { opacity: 1; transform: translateY(0); transition-delay: 0.58s; }

@media (max-width: 768px) {
  .hero-content    { margin-top: 3vh; }
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 18px;
  background: rgba(37, 99, 235, 0.1);
  border: 1px solid rgba(96, 165, 250, 0.25);
  border-radius: 50px;
  backdrop-filter: blur(10px);
  font-size: 13px;
  font-weight: 600;
  color: #60A5FA;
  letter-spacing: 0.5px;
  margin-bottom: 32px;
  animation: badge-glow 3.5s ease-in-out 1s infinite;
}

@keyframes badge-glow {
  0%, 100% { box-shadow: 0 0 0 0 rgba(37, 99, 235, 0); }
  50%       { box-shadow: 0 0 24px rgba(37, 99, 235, 0.25), 0 0 8px rgba(96, 165, 250, 0.15); }
}

@media (hover: hover) {
  .hero-badge:hover {
    border-color: rgba(96, 165, 250, 0.4);
    background: rgba(37, 99, 235, 0.16);
    transition: border-color 0.3s ease, background 0.3s ease;
  }
}

.badge-dot {
  color: #60A5FA;
  font-size: 11px;
}

.hero-title {
  font-size: clamp(38px, 6vw, 65px);
  font-weight: 500;
  color: #F8FAFC;
  line-height: 1.1;
  letter-spacing: -2px;
  margin-bottom: 24px;
  margin-top: 70px;
  width: min(1200px, 95vw);
  margin-left: calc((min(1200px, 95vw) - 100%) / -2);
  margin-right: calc((min(1200px, 95vw) - 100%) / -2);
}


.hero-subtitle {
  font-size: clamp(16px, 2.2vw, 18px);
  color: rgba(248, 250, 252, 0.65);
  line-height: 1.7;
  max-width: 680px;
  margin: 0 auto 40px;
}

.hero-actions {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  margin-bottom: 48px;
  flex-wrap: wrap;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 15px;
  font-weight: 600;
  border-radius: 50px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 0 0 0 rgba(37, 99, 235, 0);
  position: relative;
  overflow: hidden;
}

.btn-primary::after {
  content: '';
  position: absolute;
  top: -60%;
  left: -80%;
  width: 50%;
  height: 220%;
  background: linear-gradient(105deg, transparent, rgba(255, 255, 255, 0.28), transparent);
  transform: skewX(-20deg);
  pointer-events: none;
}

@media (hover: hover) {
  .btn-primary:hover {
    transform: scale(1.03);
    box-shadow: 0 0 32px rgba(37, 99, 235, 0.7), 0 4px 20px rgba(37, 99, 235, 0.4);
    background: #1d4ed8;
  }
  .btn-primary:hover::after {
    animation: btn-shimmer 0.55s ease forwards;
  }
}

@keyframes btn-shimmer {
  to { left: 130%; }
}

.btn-arrow {
  font-size: 18px;
  transition: transform 0.3s ease;
}

@media (hover: hover) {
  .btn-primary:hover .btn-arrow {
    transform: translateX(4px);
  }
}

.btn-secondary {
  display: inline-flex;
  align-items: center;
  padding: 16px 32px;
  background: transparent;
  color: rgba(248, 250, 252, 0.8);
  font-size: 15px;
  font-weight: 600;
  border-radius: 50px;
  border: 2.5px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

@media (hover: hover) {
  .btn-secondary:hover {
    border-color: rgba(255, 255, 255, 0.5);
    color: #F8FAFC;
    background: rgba(255, 255, 255, 0.05);
    transform: scale(1.02);
  }
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  width: 100%;
  margin-top: 80px;
}

.stat-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 32px 24px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 20px;
}

.stat-number {
  font-size: clamp(36px, 5vw, 56px);
  font-weight: 400;
  color: #F8FAFC;
  line-height: 1;
  letter-spacing: -2px;
}

.stat-label {
  font-size: 14px;
  font-weight: 400;
  color: rgba(248, 250, 252, 0.45);
  letter-spacing: 0.2px;
}

@media (max-width: 768px) {
  .hero-stats {
    grid-template-columns: 1fr;
    gap: 12px;
  }

  .stat-card {
    padding: 30px 20px;
  }

  .hero-title {
    margin-top: 0;
  }
}


.desktop-only {
  display: block;
}

.desktop-br {
  display: inline;
}

@media (max-width: 768px) {
  .desktop-br {
    display: none;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 100px 20px 60px;
  }

  .hero-title {
    letter-spacing: -1px;
  }
  .hero-gradient {
    display: block;
  }

  .desktop-only {
    display: none;
  }


  .hero-badge {
    font-size: 11px;
    letter-spacing: 0;
    padding: 7px 14px;
    white-space: nowrap;
  }
}

/* ── Scroll indicator ── */
.hero-scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  opacity: 0;
  animation: fade-in-delayed 0.6s ease 1.6s forwards;
}

@keyframes fade-in-delayed {
  to { opacity: 1; }
}

.scroll-pill {
  width: 26px;
  height: 44px;
  border: 2px solid rgba(255, 255, 255, 0.18);
  border-radius: 13px;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding-top: 7px;
}

.scroll-pill-dot {
  width: 4px;
  height: 8px;
  background: #60A5FA;
  border-radius: 2px;
  animation: scroll-dot 2.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) 2.2s infinite;
  opacity: 0;
}

@keyframes scroll-dot {
  0%  { transform: translateY(0);    opacity: 0; }
  15% { opacity: 1; }
  80% { transform: translateY(14px); opacity: 0; }
  81% { transform: translateY(0);    opacity: 0; }
  100%{ transform: translateY(0);    opacity: 0; }
}

@media (max-width: 768px) {
  .hero-scroll-indicator {
    display: none;
  }
}
</style>
