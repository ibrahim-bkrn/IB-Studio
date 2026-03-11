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
          IB Studio — Création Web &amp; Solutions Digitales
        </div>

        <h1 class="hero-title">
          Votre présence en ligne,<br />
          pensée pour <span class="hero-gradient">{{ currentWord }}<span class="cursor-blink">|</span></span>
        </h1>

        <p class="hero-subtitle">
          Je crée des sites web qui attirent, convainquent et convertissent —<br class="desktop-only" />
          sur-mesure ou sur CMS, toujours pensés pour votre business.
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

    <div class="hero-scroll-indicator" aria-hidden="true">
      <div class="scroll-pill">
        <div class="scroll-pill-dot"></div>
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
  mask-image: radial-gradient(ellipse 80% 70% at 50% 45%, black 20%, transparent 75%);
  -webkit-mask-image: radial-gradient(ellipse 80% 70% at 50% 45%, black 20%, transparent 75%);
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

.hero-badge,
.hero-title,
.hero-subtitle,
.hero-actions,
.hero-trust {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.75s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.75s cubic-bezier(0.4, 0, 0.2, 1);
}

.hero-content.visible .hero-badge    { opacity: 1; transform: translateY(0); transition-delay: 0.08s; }
.hero-content.visible .hero-title    { opacity: 1; transform: translateY(0); transition-delay: 0.26s; }
.hero-content.visible .hero-subtitle { opacity: 1; transform: translateY(0); transition-delay: 0.44s; }
.hero-content.visible .hero-actions  { opacity: 1; transform: translateY(0); transition-delay: 0.58s; }
.hero-content.visible .hero-trust    { opacity: 1; transform: translateY(0); transition-delay: 0.72s; }

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
  font-size: clamp(44px, 7vw, 72px);
  font-weight: 800;
  color: #F8FAFC;
  line-height: 1.1;
  letter-spacing: -2px;
  margin-bottom: 24px;
}

.hero-gradient {
  background: linear-gradient(270deg, #2563EB, #60A5FA, #c4b5fd, #60A5FA, #2563EB);
  background-size: 400% 400%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradient-shift 6s ease infinite;
  filter: drop-shadow(0 0 20px rgba(96, 165, 250, 0.3));
}

@keyframes gradient-shift {
  0%   { background-position: 0% 50%; }
  50%  { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
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
  border: 1px solid rgba(255, 255, 255, 0.2);
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

.hero-trust {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  list-style: none;
  flex-wrap: wrap;
}

.hero-trust li {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 12.5px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.55);
  letter-spacing: 0.3px;
  padding: 6px 14px;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 50px;
  background: rgba(255, 255, 255, 0.03);
}

.trust-check {
  color: #60A5FA;
  font-size: 13px;
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
