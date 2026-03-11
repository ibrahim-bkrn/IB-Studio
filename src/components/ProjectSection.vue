<template>
  <section class="projects" aria-labelledby="projects-title">
    <div class="projects-orb projects-orb--1" aria-hidden="true"></div>
    <div class="projects-orb projects-orb--2" aria-hidden="true"></div>

    <div ref="sectionEl" class="projects-container" :class="{ visible: isVisible }">
      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Mon approche</span>
        <h2 id="projects-title" class="section-title">Votre projet, votre solution</h2>
        <p class="section-subtitle">
          Je construis ce dont vous avez besoin — pas ce qui est le plus simple à livrer.
        </p>
      </div>

      <p class="projects-intro">
        Vitrine, boutique, refonte, outil métier ou plateforme communautaire :
        je dimensionne chaque projet à votre réalité, votre budget et vos objectifs.
      </p>

      <div class="projects-grid" role="list">
        <article
          v-for="(project, i) in projects"
          :key="project.type"
          class="project-card"
          :style="{ transitionDelay: `${i * 80}ms` }"
          role="listitem"
        >
          <span class="project-icon" aria-hidden="true">{{ project.icon }}</span>
          <div class="project-info">
            <h3 class="project-type">{{ project.type }}</h3>
            <p class="project-desc">{{ project.desc }}</p>
          </div>
        </article>
      </div>

      <div class="projects-note">
        <p>Chaque solution est entièrement personnalisable et tarifée sur devis.</p>
        <p>Contactez-moi pour un devis précis, <strong>gratuit et sans engagement.</strong></p>
      </div>

      <div class="projects-cta">
        <a href="#contact" class="btn-cta" aria-label="Demander un devis gratuit">
          Demander un devis gratuit
          <span aria-hidden="true">→</span>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.08 })

const projects = [
  {
    icon: '◻',
    type: 'Site vitrine',
    desc: 'Présence pro, crédibilité immédiate, jusqu\'à 5–7 pages',
  },
  {
    icon: '◈',
    type: 'E-commerce',
    desc: 'Boutique en ligne optimisée pour vendre',
  },
  {
    icon: '↺',
    type: 'Refonte',
    desc: 'Moderniser l\'existant, améliorer l\'UX et les performances',
  },
  {
    icon: '⊞',
    type: 'CRM / Outil métier',
    desc: 'Automatiser et organiser votre activité en ligne',
  },
  {
    icon: '◉',
    type: 'Forum / Communauté',
    desc: 'Créer un espace d\'échange autour de votre marque',
  },
]
</script>

<style scoped>
.projects {
  background: #0A0F1E;
  padding: 120px 24px;
  position: relative;
  overflow: hidden;
}

.projects-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
}

.projects-orb--1 {
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.2) 0%, transparent 70%);
  top: -200px;
  right: -200px;
}

.projects-orb--2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(79, 70, 229, 0.15) 0%, transparent 70%);
  bottom: -100px;
  left: -100px;
}

.projects-container {
  max-width: 1100px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1), transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.projects-container.visible {
  opacity: 1;
  transform: translateY(0);
}

.section-header {
  text-align: center;
  margin-bottom: 40px;
}

.section-label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #60A5FA;
  display: block;
  margin-bottom: 16px;
}

.section-title {
  font-size: clamp(36px, 5vw, 48px);
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -1.5px;
  margin-bottom: 16px;
}

.section-subtitle {
  font-size: 17px;
  color: rgba(248, 250, 252, 0.6);
  font-style: italic;
  max-width: 560px;
  margin: 0 auto;
  line-height: 1.7;
}

.projects-intro {
  text-align: center;
  font-size: 16px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.8;
  max-width: 720px;
  margin: 0 auto 64px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-bottom: 48px;
}

/* Last row: 2 items centered */
.project-card:nth-child(4),
.project-card:nth-child(5) {
  grid-column: span 1;
}

.projects-grid::after {
  content: '';
  grid-column: span 0;
}

/* Center last 2 cards */
@supports (display: grid) {
  .projects-grid {
    grid-template-columns: repeat(6, 1fr);
  }

  .project-card:nth-child(1) { grid-column: 1 / 3; }
  .project-card:nth-child(2) { grid-column: 3 / 5; }
  .project-card:nth-child(3) { grid-column: 5 / 7; }
  .project-card:nth-child(4) { grid-column: 2 / 4; }
  .project-card:nth-child(5) { grid-column: 4 / 6; }
}

.project-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 18px;
  padding: 28px 28px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: default;
}

@media (hover: hover) {
  .project-card:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(96, 165, 250, 0.3);
    box-shadow: 0 0 30px rgba(37, 99, 235, 0.15), inset 0 1px 0 rgba(255, 255, 255, 0.1);
  }
}

.project-icon {
  font-size: 22px;
  color: #60A5FA;
  flex-shrink: 0;
  width: 44px;
  height: 44px;
  background: rgba(37, 99, 235, 0.15);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

@media (hover: hover) {
  .project-card:hover .project-icon {
    background: rgba(37, 99, 235, 0.25);
  }
}

.project-type {
  font-size: 16px;
  font-weight: 700;
  color: #F8FAFC;
  margin-bottom: 6px;
  letter-spacing: -0.3px;
}

.project-desc {
  font-size: 13.5px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.6;
}

.projects-note {
  text-align: center;
  margin-bottom: 40px;
}

.projects-note p {
  font-size: 15px;
  color: rgba(248, 250, 252, 0.5);
  line-height: 1.7;
}

.projects-note strong {
  color: rgba(248, 250, 252, 0.8);
  font-weight: 600;
}

.projects-cta {
  display: flex;
  justify-content: center;
}

.btn-cta {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 36px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 15px;
  font-weight: 600;
  border-radius: 50px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 0 0 0 rgba(37, 99, 235, 0);
}

@media (hover: hover) {
  .btn-cta:hover {
    transform: scale(1.03);
    box-shadow: 0 0 32px rgba(37, 99, 235, 0.7), 0 4px 20px rgba(37, 99, 235, 0.4);
    background: #1d4ed8;
  }
}

@media (max-width: 1024px) {
  .projects-grid,
  .projects-grid:not(.desktop) {
    grid-template-columns: repeat(2, 1fr);
  }

  .project-card:nth-child(1) { grid-column: auto; }
  .project-card:nth-child(2) { grid-column: auto; }
  .project-card:nth-child(3) { grid-column: auto; }
  .project-card:nth-child(4) { grid-column: auto; }
  .project-card:nth-child(5) { grid-column: auto; }
}

@media (max-width: 768px) {
  .projects {
    padding: 80px 20px;
  }

  .projects-grid {
    grid-template-columns: 1fr !important;
  }

  .project-card:nth-child(n) {
    grid-column: auto !important;
  }
}

/* ── Auto-animations sur touch ── */
@media (hover: none) {
  /* Carte — lift + glow cyclique */
  .project-card:nth-child(1) { animation: auto-project-card 10s ease-in-out infinite 1.5s; }
  .project-card:nth-child(2) { animation: auto-project-card 10s ease-in-out infinite 3.5s; }
  .project-card:nth-child(3) { animation: auto-project-card 10s ease-in-out infinite 5.5s; }
  .project-card:nth-child(4) { animation: auto-project-card 10s ease-in-out infinite 7.5s; }
  .project-card:nth-child(5) { animation: auto-project-card 10s ease-in-out infinite 9.5s; }

  /* Icône */
  .project-card:nth-child(1) .project-icon { animation: auto-project-icon 10s ease-in-out infinite 1.5s; }
  .project-card:nth-child(2) .project-icon { animation: auto-project-icon 10s ease-in-out infinite 3.5s; }
  .project-card:nth-child(3) .project-icon { animation: auto-project-icon 10s ease-in-out infinite 5.5s; }
  .project-card:nth-child(4) .project-icon { animation: auto-project-icon 10s ease-in-out infinite 7.5s; }
  .project-card:nth-child(5) .project-icon { animation: auto-project-icon 10s ease-in-out infinite 9.5s; }
}

@keyframes auto-project-card {
  0%, 15% {
    transform: translateY(0);
    background: rgba(255, 255, 255, 0.05);
    border-color: rgba(255, 255, 255, 0.1);
    box-shadow: none;
  }
  25%, 35% {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(96, 165, 250, 0.3);
    box-shadow: 0 0 30px rgba(37, 99, 235, 0.18), inset 0 1px 0 rgba(255, 255, 255, 0.1);
  }
  50%, 100% {
    transform: translateY(0);
    background: rgba(255, 255, 255, 0.05);
    border-color: rgba(255, 255, 255, 0.1);
    box-shadow: none;
  }
}

@keyframes auto-project-icon {
  0%, 15%  { background: rgba(37, 99, 235, 0.15); }
  25%, 35% { background: rgba(37, 99, 235, 0.28); }
  50%, 100% { background: rgba(37, 99, 235, 0.15); }
}
</style>
