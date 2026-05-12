<template>
  <section class="differential" aria-labelledby="diff-title">
    <div class="diff-orb diff-orb--1" aria-hidden="true"></div>
    <div class="diff-orb diff-orb--2" aria-hidden="true"></div>

    <div ref="sectionEl" class="diff-container" :class="{ visible: isVisible }">

      <div class="diff-header">
        <span class="diff-label" aria-hidden="true">— Pourquoi moi</span>
        <h2 id="diff-title" class="diff-title">
          Pourquoi choisir<br class="mobile-break" /> IB Studio ?
        </h2>
        <p class="diff-subtitle"> 
          Voici ce qui me différencie.
        </p>
      </div>

      <div class="diff-grid">
        <div
          v-for="(point, i) in points"
          :key="i"
          class="diff-card"
          :class="`diff-delay-${i}`"
        >
          <div class="diff-icon" aria-hidden="true">{{ point.icon }}</div>
          <h3 class="diff-card-title">{{ point.title }}</h3>
          <p class="diff-card-text">{{ point.text }}</p>
        </div>
      </div>

      <div class="diff-launch" aria-label="Offre de lancement">
        <div class="launch-left">
          <span class="launch-badge">Offre de lancement</span>
          <p class="launch-text">
            Je construis mon portfolio — les <strong>premiers projets</strong> bénéficient
            de <strong>tarifs préférentiels.</strong>
            Même engagement qualité. Places limitées.
          </p>
        </div>
        <a href="#contact" class="launch-cta">
          Profiter de l'offre
        </a>
      </div>

    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.08 })

const points = [
  {
    icon: '🤝',
    title: 'Je m\'occupe de votre projet comme si c\'était le mien',
    text: 'Je m\'adapte à vous, pas l\'inverse. Pas de process compliqué, pas de réunions inutiles — je comprends votre besoin, je m\'adapte à votre situation et à votre disponibilité.',
  },
  {
    icon: '🚀',
    title: 'La qualité d\'une agence, le prix d\'un freelance',
    text: 'Résultat professionnel, design soigné, site performant — sans les marges ni les intermédiaires d\'une agence traditionnelle.',
  },
  {
    icon: '🎓',
    title: 'Formation ingénieur, méthode éprouvée',
    text: 'Grande école du numérique : rigueur, respect des délais, livrables clairs. Vous ne misez pas sur un amateur qui improvise.',
  },
]
</script>

<style scoped>
.differential {
  background: #0A0F1E;
  padding: 120px 24px;
  position: relative;
  /* débordement haut autorisé (orbe bleue remonte dans la section sombre précédente)
     débordement bas clippé (ne saigne pas sur la section blanche) */
  overflow: visible;
  clip-path: inset(-400px 0px 0px 0px);
}

/* Orbes */
.diff-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
}

.diff-orb--1 {
  width: 550px;
  height: 550px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.18) 0%, transparent 70%);
  top: -150px;
  right: -100px;
}

.diff-orb--2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(139, 92, 246, 0.12) 0%, transparent 70%);
  bottom: -80px;
  left: -80px;
}

/* Container */
.diff-container {
  max-width: 1100px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.diff-container.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Header */
.mobile-break { display: none; }

/*.diff-title-sub {
  font-size: 0.9em;
}*/

.diff-header {
  text-align: center;
  margin-bottom: 72px;
}

.diff-label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #60A5FA;
  display: block;
  margin-bottom: 16px;
}

.diff-title {
  font-size: clamp(36px, 5vw, 52px);
  font-weight: 800;
  color: #F8FAFC;
  letter-spacing: -2px;
  line-height: 1.1;
  margin-bottom: 20px;
  position: relative;
  display: inline-block;
}

.diff-title::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 2px;
  transition: width 0.7s cubic-bezier(0.4, 0, 0.2, 1) 0.5s;
}

.diff-container.visible .diff-title::after {
  width: 64px;
}

.diff-subtitle {
  font-size: 17px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.7;
  max-width: 480px;
  margin: 0 auto;
}

/* Cards */
.diff-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-bottom: 48px;
}

.diff-card {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  padding: 36px 30px;
  position: relative;
  overflow: hidden;
  opacity: 0;
  animation: diff-card-enter 0.6s cubic-bezier(0.4, 0, 0.2, 1) both;
  transition: border-color 0.3s ease, background 0.3s ease;
}

.diff-container:not(.visible) .diff-card {
  animation: none;
}

.diff-container.visible .diff-delay-0 { animation-delay: 0.1s; }
.diff-container.visible .diff-delay-1 { animation-delay: 0.22s; }
.diff-container.visible .diff-delay-2 { animation-delay: 0.34s; }

@keyframes diff-card-enter {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

.diff-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0), transparent);
  transition: background 0.4s ease;
}

@media (hover: hover) {
  .diff-card:hover {
    background: rgba(255, 255, 255, 0.07);
    border-color: rgba(37, 99, 235, 0.25);
  }
  .diff-card:hover::before {
    background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.6), transparent);
  }
  .diff-card:hover .diff-icon {
    background: rgba(37, 99, 235, 0.2);
    color: #60A5FA;
  }
}

.diff-icon {
  width: 48px;
  height: 48px;
  background: rgba(37, 99, 235, 0.1);
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  color: #60A5FA;
  margin-bottom: 20px;
  transition: all 0.3s ease;
}

.diff-card-title {
  font-size: 17px;
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -0.5px;
  margin-bottom: 12px;
  line-height: 1.3;
}

.diff-card-text {
  font-size: 14.5px;
  color: rgba(248, 250, 252, 0.5);
  line-height: 1.75;
}

/* Launch offer banner */
.diff-launch {
  display: flex;
  align-items: center;
  gap: 32px;
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.12) 0%, rgba(79, 70, 229, 0.08) 100%);
  border: 1px solid rgba(37, 99, 235, 0.3);
  border-radius: 20px;
  padding: 32px 40px;
  position: relative;
  overflow: hidden;
}

.diff-launch::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 60% 80% at 0% 50%, rgba(37, 99, 235, 0.08), transparent);
  pointer-events: none;
}

.launch-left {
  flex: 1;
}

.launch-badge {
  display: inline-flex;
  align-items: center;
  padding: 4px 12px;
  background: rgba(37, 99, 235, 0.2);
  border: 1px solid rgba(37, 99, 235, 0.4);
  border-radius: 50px;
  font-size: 11.5px;
  font-weight: 700;
  color: #60A5FA;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 12px;
  animation: badge-glow 3s ease-in-out infinite;
}

@keyframes badge-glow {
  0%, 100% { box-shadow: 0 0 0 0 rgba(37, 99, 235, 0); }
  50%       { box-shadow: 0 0 16px rgba(37, 99, 235, 0.3); }
}

.launch-text {
  font-size: 15px;
  color: rgba(248, 250, 252, 0.7);
  line-height: 1.65;
}

.launch-text strong {
  color: #F8FAFC;
  font-weight: 600;
}

.launch-cta {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 14px 28px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  white-space: nowrap;
  flex-shrink: 0;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

@media (hover: hover) {
  .launch-cta:hover {
    background: #1d4ed8;
    transform: scale(1.03);
    box-shadow: 0 0 24px rgba(37, 99, 235, 0.5);
  }
}

/* Auto-animations touch */
@media (hover: none) {
  .diff-container.visible .diff-card {
    opacity: 1;
  }
  .diff-delay-0 { animation: auto-diff-card 9s ease-in-out infinite 1.5s; }
  .diff-delay-1 { animation: auto-diff-card 9s ease-in-out infinite 4.5s; }
  .diff-delay-2 { animation: auto-diff-card 9s ease-in-out infinite 7.5s; }
}

@keyframes auto-diff-card {
  0%, 15%  { background: rgba(255, 255, 255, 0.04); border-color: rgba(255, 255, 255, 0.08); }
  28%, 38% { background: rgba(255, 255, 255, 0.07); border-color: rgba(37, 99, 235, 0.25); }
  52%, 100% { background: rgba(255, 255, 255, 0.04); border-color: rgba(255, 255, 255, 0.08); }
}

/* Responsive */
@media (max-width: 1024px) {
  .diff-grid {
    grid-template-columns: 1fr 1fr;
  }

  .diff-card:last-child {
    grid-column: span 2;
    max-width: 480px;
    margin: 0 auto;
    width: 100%;
  }
}

@media (max-width: 768px) {
  .mobile-break { display: block; }

  .differential {
    padding: 80px 20px;
  }

  .diff-grid {
    grid-template-columns: 1fr;
  }

  .diff-card:last-child {
    grid-column: span 1;
    max-width: unset;
  }

  .diff-launch {
    flex-direction: column;
    align-items: flex-start;
    padding: 28px 24px;
    gap: 20px;
  }

  .launch-cta {
    width: 100%;
    justify-content: center;
  }

  .diff-header {
    margin-bottom: 48px;
  }
}
</style>
