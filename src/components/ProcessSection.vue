<template>
  <section class="process" aria-labelledby="process-title">
    <div class="process-orb process-orb--1" aria-hidden="true"></div>
    <div class="process-orb process-orb--2" aria-hidden="true"></div>

    <div ref="sectionEl" class="process-container" :class="{ visible: isVisible }">
      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Comment je travaille</span>
        <h2 id="process-title" class="section-title">Un processus clair,<br />du premier contact à la livraison.</h2>
        <p class="section-subtitle">
          Pas de surprise, pas de zone grise. Vous savez à chaque étape où on en est et quoi attendre.
        </p>
      </div>

      <div class="steps" role="list">
        <article
          v-for="(step, i) in steps"
          :key="step.number"
          class="step"
          :style="{ transitionDelay: `${i * 120}ms` }"
          role="listitem"
        >
          <div class="step-left">
            <div class="step-number" aria-hidden="true">{{ step.number }}</div>
            <div v-if="i < steps.length - 1" class="step-line" aria-hidden="true"></div>
          </div>

          <div class="step-content">
            <div class="step-icon" aria-hidden="true">{{ step.icon }}</div>
            <div class="step-body">
              <div class="step-tag">{{ step.tag }}</div>
              <h3 class="step-title">{{ step.title }}</h3>
              <p class="step-text">{{ step.text }}</p>
              <ul v-if="step.items" class="step-items" role="list">
                <li v-for="item in step.items" :key="item">{{ item }}</li>
              </ul>
            </div>
          </div>
        </article>
      </div>

      <div class="process-note">
        <span class="note-icon" aria-hidden="true">◈</span>
        Chaque projet est différent — la durée et les étapes s'adaptent à votre besoin réel.
      </div>
    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.06 })

const steps = [
  {
    number: '01',
    icon: '◎',
    tag: 'Découverte',
    title: 'On se comprend avant de construire',
    text: 'Un premier échange pour cerner votre activité, vos objectifs et votre cible. Je pose les bonnes questions dès le départ pour ne rien laisser au hasard.',
    items: ['Appel ou échange écrit', 'Analyse de votre existant', 'Définition des objectifs'],
  },
  {
    number: '02',
    icon: '✦',
    tag: 'Conception',
    title: 'Design pensé pour convertir',
    text: 'Avant de construire quoi que ce soit, je conçois la structure et l\'identité visuelle de votre projet. Vous validez chaque étape.',
    items: ['Maquettes fil de fer', 'Design UI sur Figma', 'Validation avant développement'],
  },
  {
    number: '03',
    icon: '⚡',
    tag: 'Développement',
    title: 'Réalisation soignée, performances optimales',
    text: 'Je développe votre solution avec la technologie la mieux adaptée. Chaque composant est pensé pour la rapidité, le SEO et la maintenabilité.',
    items: ['Développement itératif', 'Tests cross-navigateurs et mobile'],
  },
  {
    number: '04',
    icon: '◇',
    tag: 'Livraison',
    title: 'Mise en ligne et passation complète',
    text: 'Déploiement sur votre hébergeur, configuration du domaine, formation à la prise en main. Vous repartez autonome.',
    items: ['Déploiement & configuration', 'Formation à la gestion du contenu', 'Documentation remise'],
  },
  {
    number: '05',
    icon: '⬡',
    tag: 'Suivi',
    title: 'Je reste disponible après la livraison',
    text: 'Le projet est livré, mais la relation ne s\'arrête pas là. Évolutions, corrections, optimisations SEO — je suis là si vous en avez besoin.',
    items: ['Support réactif', 'Mises à jour et évolutions', 'Suivi des performances'],
  },
]
</script>

<style scoped>
.process {
  background: #0A0F1E;
  padding: 120px 24px;
  position: relative;
  overflow: hidden;
}

.process-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
}

.process-orb--1 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.18) 0%, transparent 70%);
  top: 0;
  left: -150px;
}

.process-orb--2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(96, 165, 250, 0.12) 0%, transparent 70%);
  bottom: 0;
  right: -100px;
}

.process-container {
  max-width: 860px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1), transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.process-container.visible {
  opacity: 1;
  transform: translateY(0);
}

.section-header {
  text-align: center;
  margin-bottom: 80px;
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
  font-size: clamp(32px, 5vw, 46px);
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -1.5px;
  line-height: 1.15;
  margin-bottom: 20px;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -6px;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 2px;
  transition: width 0.7s cubic-bezier(0.4, 0, 0.2, 1) 0.5s;
}

.process-container.visible .section-title::after {
  width: 60px;
}

.section-subtitle {
  font-size: 16px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.7;
  max-width: 500px;
  margin: 0 auto;
}

/* Steps */
.steps {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.step {
  display: grid;
  grid-template-columns: 56px 1fr;
  gap: 24px;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.step-left {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.step-number {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: rgba(37, 99, 235, 0.15);
  border: 1.5px solid rgba(37, 99, 235, 0.4);
  color: #60A5FA;
  font-size: 13px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: all 0.3s ease;
  letter-spacing: 0.5px;
}

@media (hover: hover) {
  .step:hover .step-number {
    background: rgba(37, 99, 235, 0.3);
    border-color: #2563EB;
    box-shadow: 0 0 20px rgba(37, 99, 235, 0.4);
  }
}

.step-line {
  width: 1.5px;
  flex: 1;
  min-height: 40px;
  background: linear-gradient(to bottom, rgba(37, 99, 235, 0.4), rgba(37, 99, 235, 0.08));
  margin: 8px 0;
}

.step-content {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  padding-bottom: 48px;
}

.step:last-child .step-content {
  padding-bottom: 0;
}

.step-icon {
  width: 48px;
  height: 48px;
  flex-shrink: 0;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  color: #60A5FA;
  transition: all 0.3s ease;
  margin-top: 2px;
}

@media (hover: hover) {
  .step:hover .step-icon {
    background: rgba(37, 99, 235, 0.15);
    border-color: rgba(96, 165, 250, 0.25);
  }
}

.step-body {
  flex: 1;
}

.step-tag {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  color: #2563EB;
  margin-bottom: 8px;
}

.step-title {
  font-size: 20px;
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -0.5px;
  margin-bottom: 10px;
}

.step-text {
  font-size: 15px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.75;
  margin-bottom: 16px;
}

.step-items {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.step-items li {
  font-size: 12.5px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.6);
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 5px 12px;
  border-radius: 50px;
  transition: all 0.3s ease;
}

@media (hover: hover) {
  .step:hover .step-items li {
    background: rgba(37, 99, 235, 0.1);
    border-color: rgba(96, 165, 250, 0.2);
    color: rgba(248, 250, 252, 0.8);
  }
}

.process-note {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin-top: 64px;
  font-size: 14px;
  color: rgba(248, 250, 252, 0.35);
  font-style: italic;
  text-align: center;
}

.note-icon {
  color: #2563EB;
  font-size: 16px;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .process {
    padding: 80px 20px;
  }

  .step {
    grid-template-columns: 40px 1fr;
    gap: 16px;
  }

  .step-number {
    width: 36px;
    height: 36px;
    font-size: 11px;
  }

  .step-content {
    flex-direction: column;
    gap: 12px;
    padding-bottom: 36px;
  }

  .step-icon {
    width: 40px;
    height: 40px;
    font-size: 17px;
  }

  .section-header {
    margin-bottom: 56px;
  }
}

/* ── Auto-animations sur touch ── */
@media (hover: none) {
  /* Numéro de step — glow cyclique */
  .steps .step:nth-child(1) .step-number { animation: auto-step-glow 10s ease-in-out infinite 1.5s; }
  .steps .step:nth-child(2) .step-number { animation: auto-step-glow 10s ease-in-out infinite 4s; }
  .steps .step:nth-child(3) .step-number { animation: auto-step-glow 10s ease-in-out infinite 6.5s; }
  .steps .step:nth-child(4) .step-number { animation: auto-step-glow 10s ease-in-out infinite 9s; }

  /* Icône de step — halo */
  .steps .step:nth-child(1) .step-icon { animation: auto-step-icon 10s ease-in-out infinite 1.5s; }
  .steps .step:nth-child(2) .step-icon { animation: auto-step-icon 10s ease-in-out infinite 4s; }
  .steps .step:nth-child(3) .step-icon { animation: auto-step-icon 10s ease-in-out infinite 6.5s; }
  .steps .step:nth-child(4) .step-icon { animation: auto-step-icon 10s ease-in-out infinite 9s; }
}

@keyframes auto-step-glow {
  0%, 18% {
    background: rgba(37, 99, 235, 0.15);
    border-color: rgba(37, 99, 235, 0.4);
    box-shadow: none;
  }
  28%, 38% {
    background: rgba(37, 99, 235, 0.3);
    border-color: #2563EB;
    box-shadow: 0 0 20px rgba(37, 99, 235, 0.5);
  }
  50%, 100% {
    background: rgba(37, 99, 235, 0.15);
    border-color: rgba(37, 99, 235, 0.4);
    box-shadow: none;
  }
}

@keyframes auto-step-icon {
  0%, 18%  { background: rgba(255, 255, 255, 0.05); border-color: rgba(255, 255, 255, 0.08); }
  28%, 38% { background: rgba(37, 99, 235, 0.18);   border-color: rgba(37, 99, 235, 0.35); }
  50%, 100% { background: rgba(255, 255, 255, 0.05); border-color: rgba(255, 255, 255, 0.08); }
}
</style>
