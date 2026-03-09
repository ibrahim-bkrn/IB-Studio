<template>
  <section class="hero" aria-label="Introduction">
    <div class="hero-orb hero-orb--1" aria-hidden="true" :style="orbStyle(0.02, 0.015)"></div>
    <div class="hero-orb hero-orb--2" aria-hidden="true" :style="orbStyle(-0.018, -0.012)"></div>
    <div class="hero-orb hero-orb--3" aria-hidden="true" :style="orbStyle(0.01, 0.02)"></div>
    <div class="hero-grid" aria-hidden="true"></div>

    <div class="hero-container">
      <div class="hero-content" :class="{ visible: mounted }">
        <div class="hero-badge" aria-label="Spécialité">
          <span class="badge-dot" aria-hidden="true">✦</span>
          IB Studio — Développeur Web &amp; Solutions Digitales
        </div>

        <h1 class="hero-title">
          Votre présence en ligne,<br />
          pensée pour <span class="hero-gradient">{{ currentWord }}<span class="cursor-blink">|</span></span>
        </h1>

        <p class="hero-subtitle">
          Je conçois des solutions web sur-mesure — design, développement et SEO —<br class="desktop-only" />
          pour propulser votre business en ligne et le faire croître durablement.
        </p>

        <div class="hero-actions">
          <a href="#contact" class="btn-primary" aria-label="Discuter de votre projet">
            Parlons de votre projet
            <span class="btn-arrow" aria-hidden="true">→</span>
          </a>
          <a href="#services" class="btn-secondary" aria-label="Voir les services proposés">
            Voir mes services
          </a>
        </div>

        <ul class="hero-trust" role="list" aria-label="Indicateurs de confiance">
          <li>
            <span class="trust-check" aria-hidden="true">✓</span>
            3 ans d'expérience
          </li>
          <li>
            <span class="trust-check" aria-hidden="true">✓</span>
            Grande école d'ingénieur
          </li>
          <li>
            <span class="trust-check" aria-hidden="true">✓</span>
            Réponse sous 24h
          </li>
        </ul>
      </div>
    </div>
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

// Typing effect
const words = ['performer.', 'convertir.', 'grandir.', 'durer.']
const currentWord = ref('')
let wordIndex = 0
let charIndex = 0
let isDeleting = false
let typingTimer = null

function type() {
  const target = words[wordIndex]

  if (!isDeleting) {
    currentWord.value = target.slice(0, charIndex + 1)
    charIndex++
    if (charIndex === target.length) {
      isDeleting = true
      typingTimer = setTimeout(type, 2000) // pause avant d'effacer
      return
    }
  } else {
    currentWord.value = target.slice(0, charIndex - 1)
    charIndex--
    if (charIndex === 0) {
      isDeleting = false
      wordIndex = (wordIndex + 1) % words.length
    }
  }

  typingTimer = setTimeout(type, isDeleting ? 60 : 90)
}

onMounted(() => {
  requestAnimationFrame(() => {
    mounted.value = true
  })
  typingTimer = setTimeout(type, 1800)
  window.addEventListener('mousemove', onMouseMove, { passive: true })
})

onUnmounted(() => {
  clearTimeout(typingTimer)
  window.removeEventListener('mousemove', onMouseMove)
})
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
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
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.35) 0%, transparent 70%);
  top: -100px;
  left: -100px;
  animation: orb-float 8s ease-in-out infinite;
}

.hero-orb--2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(96, 165, 250, 0.2) 0%, transparent 70%);
  bottom: 0;
  right: -80px;
  animation: orb-float 10s ease-in-out infinite reverse;
}

.hero-orb--3 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(79, 70, 229, 0.25) 0%, transparent 70%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: orb-pulse 6s ease-in-out infinite;
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
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
}

.hero-container {
  max-width: 900px;
  width: 100%;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  text-align: center;
}

/* Animations au chargement */
.hero-content {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.hero-content.visible {
  opacity: 1;
  transform: translateY(0);
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 18px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 50px;
  backdrop-filter: blur(10px);
  font-size: 13px;
  font-weight: 600;
  color: #60A5FA;
  letter-spacing: 0.5px;
  margin-bottom: 32px;
  transition: all 0.3s ease;
}

.hero-badge:hover {
  border-color: rgba(96, 165, 250, 0.3);
  background: rgba(37, 99, 235, 0.1);
}

.badge-dot {
  color: #60A5FA;
  font-size: 11px;
}

.hero-title {
  font-size: clamp(44px, 7vw, 72px);
  font-weight: 800;
  color: #F8FAFC;
  line-height: 1.1;
  letter-spacing: -2px;
  margin-bottom: 24px;
}

.hero-gradient {
  background: linear-gradient(135deg, #2563EB 0%, #60A5FA 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
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
}

.btn-primary:hover {
  transform: scale(1.03);
  box-shadow: 0 0 32px rgba(37, 99, 235, 0.7), 0 4px 20px rgba(37, 99, 235, 0.4);
  background: #1d4ed8;
}

.btn-arrow {
  font-size: 18px;
  transition: transform 0.3s ease;
}

.btn-primary:hover .btn-arrow {
  transform: translateX(4px);
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
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-secondary:hover {
  border-color: rgba(255, 255, 255, 0.5);
  color: #F8FAFC;
  background: rgba(255, 255, 255, 0.05);
  transform: scale(1.02);
}

.hero-trust {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 32px;
  list-style: none;
  flex-wrap: wrap;
}

.hero-trust li {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.5);
  letter-spacing: 0.3px;
}

.trust-check {
  color: #60A5FA;
  font-size: 14px;
}

.cursor-blink {
  display: inline-block;
  width: 3px;
  margin-left: 2px;
  animation: blink 0.9s step-end infinite;
  -webkit-text-fill-color: #60A5FA;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.desktop-only {
  display: block;
}

@media (max-width: 768px) {
  .hero {
    padding: 100px 20px 60px;
  }

  .hero-title {
    letter-spacing: -1px;
  }

  .desktop-only {
    display: none;
  }

  .hero-trust {
    gap: 20px;
  }
}
</style>
