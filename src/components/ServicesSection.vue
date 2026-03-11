<template>
  <section class="services" aria-labelledby="services-title">
    <div ref="sectionEl" class="services-container" :class="{ visible: isVisible }">
      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Services</span>
        <h2 id="services-title" class="section-title">Ce que je propose</h2>
        <p class="section-subtitle">
          Design, développement, SEO — tout ce qu'il faut pour que votre site travaille pour vous.
        </p>
      </div>

      <div class="services-grid" role="list">
        <article
          v-for="(service, i) in services"
          :key="service.title"
          class="service-card"
          :style="tiltStyles[i]"
          :class="`card-delay-${i}`"
          role="listitem"
          @mousemove="onTiltMove(i, $event)"
          @mouseleave="onTiltLeave(i)"
        >
          <span class="card-num" aria-hidden="true">0{{ i + 1 }}</span>
          <div class="card-icon" aria-hidden="true">{{ service.icon }}</div>
          <h3 class="card-title">{{ service.title }}</h3>
          <p class="card-text">{{ service.text }}</p>
          <div class="card-line" aria-hidden="true"></div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.1 })

// Tilt 3D
const tiltStyles = ref(Array(4).fill({}))

function onTiltMove(i, e) {
  const card = e.currentTarget
  const rect = card.getBoundingClientRect()
  const cx = rect.left + rect.width / 2
  const cy = rect.top + rect.height / 2
  const dx = (e.clientX - cx) / (rect.width / 2)
  const dy = (e.clientY - cy) / (rect.height / 2)
  tiltStyles.value[i] = {
    transform: `perspective(900px) rotateY(${dx * 6}deg) rotateX(${-dy * 5}deg) translateY(-6px)`,
    transition: 'transform 0.1s ease',
  }
}

function onTiltLeave(i) {
  tiltStyles.value[i] = {
    transform: 'perspective(900px) rotateY(0deg) rotateX(0deg) translateY(0px)',
    transition: 'transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94)',
  }
}

const services = [
  {
    icon: '✦',
    title: 'Conception & Design',
    text: 'Une identité visuelle forte et cohérente, pensée pour marquer les esprits et renforcer la crédibilité de votre marque.',
  },
  {
    icon: '⚡',
    title: 'Réalisation sur-mesure',
    text: 'L\'outil choisi selon votre projet — pas l\'inverse. WordPress, CMS, e-commerce ou solution spécifique : ce qui correspond à votre besoin et votre budget.',
  },
  {
    icon: '◎',
    title: 'Référencement SEO',
    text: 'Pour être trouvé par vos clients, pas seulement visible. Une stratégie de référencement intégrée dès la conception.',
  },
  {
    icon: '⬡',
    title: 'Suivi & Maintenance',
    text: 'Je reste disponible après la livraison. Mises à jour, évolutions, support — votre site grandit avec votre business.',
  },
]
</script>

<style scoped>
.services {
  background: #F8FAFC;
  padding: 120px 24px;
  position: relative;
  overflow: hidden;
}

.services::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 800px;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.3), transparent);
}

.services-container {
  max-width: 1100px;
  margin: 0 auto;
}

.section-header {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.services-container.visible .section-header {
  opacity: 1;
  transform: translateY(0);
}

.section-header {
  text-align: center;
  margin-bottom: 72px;
}

.section-label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #2563EB;
  display: block;
  margin-bottom: 16px;
}

.section-title {
  font-size: clamp(36px, 5vw, 48px);
  font-weight: 700;
  color: #0A0F1E;
  letter-spacing: -1.5px;
  margin-bottom: 16px;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -6px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 2px;
  transition: width 0.7s cubic-bezier(0.4, 0, 0.2, 1) 0.5s;
}

.services-container.visible .section-title::after {
  width: 60px;
}

.section-subtitle {
  font-size: 17px;
  color: #64748B;
  font-style: italic;
  max-width: 520px;
  margin: 0 auto;
  line-height: 1.7;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}

/* Entrée en stagger par carte */
.service-card {
  background: #FFFFFF;
  border: 1px solid rgba(10, 15, 30, 0.07);
  border-radius: 20px;
  padding: 40px 36px;
  position: relative;
  overflow: hidden;
  cursor: default;
  transition: box-shadow 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              border-color 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.1s ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04), 0 4px 16px rgba(0, 0, 0, 0.04);
  opacity: 0;
  animation: card-enter 0.65s cubic-bezier(0.4, 0, 0.2, 1) both;
}

.services-container:not(.visible) .service-card {
  animation: none;
}

.services-container.visible .card-delay-0 { animation-delay: 0.05s; }
.services-container.visible .card-delay-1 { animation-delay: 0.18s; }
.services-container.visible .card-delay-2 { animation-delay: 0.31s; }
.services-container.visible .card-delay-3 { animation-delay: 0.44s; }

@keyframes card-enter {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}

.service-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.04) 0%, transparent 60%);
  border-radius: 20px;
  opacity: 0;
  transition: opacity 0.3s ease;
}

@media (hover: hover) {
  .service-card:hover {
    box-shadow: 0 8px 40px rgba(37, 99, 235, 0.14), 0 2px 8px rgba(0, 0, 0, 0.06);
    border-color: rgba(37, 99, 235, 0.22);
  }
  .service-card:hover::before { opacity: 1; }
  .service-card:hover .card-icon {
    background: rgba(37, 99, 235, 0.15);
    transform: scale(1.05);
  }
  .service-card:hover .card-line { width: 100%; }
  .service-card:hover .card-num {
    color: rgba(37, 99, 235, 0.08);
  }
}

/* Numéro décoratif */
.card-num {
  position: absolute;
  top: 16px;
  right: 22px;
  font-size: 72px;
  font-weight: 800;
  color: rgba(10, 15, 30, 0.04);
  letter-spacing: -5px;
  line-height: 1;
  pointer-events: none;
  user-select: none;
  transition: color 0.3s ease;
  font-variant-numeric: tabular-nums;
}

.card-icon {
  font-size: 28px;
  margin-bottom: 20px;
  color: #2563EB;
  display: flex;
  align-items: center;
  width: 52px;
  height: 52px;
  background: rgba(37, 99, 235, 0.08);
  border-radius: 14px;
  justify-content: center;
  transition: all 0.3s ease;
}

.card-title {
  font-size: 20px;
  font-weight: 700;
  color: #0A0F1E;
  margin-bottom: 12px;
  letter-spacing: -0.5px;
}

.card-text {
  font-size: 15px;
  color: #64748B;
  line-height: 1.7;
}

.card-line {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3px;
  width: 0;
  background: linear-gradient(90deg, #2563EB, #60A5FA);
  border-radius: 0 0 0 20px;
  transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

/* ── Auto-animations sur touch (pas de hover) ── */
@media (hover: none) {
  /* Ligne bleue du bas — cycle automatique */
  .card-delay-0 .card-line { animation: auto-card-line 8s ease infinite 1.5s; }
  .card-delay-1 .card-line { animation: auto-card-line 8s ease infinite 3.5s; }
  .card-delay-2 .card-line { animation: auto-card-line 8s ease infinite 5.5s; }
  .card-delay-3 .card-line { animation: auto-card-line 8s ease infinite 7.5s; }

  /* Icône — scale + glow */
  .card-delay-0 .card-icon { animation: auto-card-icon 8s ease infinite 1.5s; }
  .card-delay-1 .card-icon { animation: auto-card-icon 8s ease infinite 3.5s; }
  .card-delay-2 .card-icon { animation: auto-card-icon 8s ease infinite 5.5s; }
  .card-delay-3 .card-icon { animation: auto-card-icon 8s ease infinite 7.5s; }
}

@keyframes auto-card-line {
  0%, 10%  { width: 0; }
  22%      { width: 100%; }
  32%      { width: 100%; }
  44%, 100% { width: 0; }
}

@keyframes auto-card-icon {
  0%, 10%  { transform: scale(1);    background: rgba(37, 99, 235, 0.08); }
  22%, 32% { transform: scale(1.08); background: rgba(37, 99, 235, 0.18); }
  44%, 100% { transform: scale(1);   background: rgba(37, 99, 235, 0.08); }
}

@media (max-width: 768px) {
  .services {
    padding: 80px 20px;
  }

  .services-grid {
    grid-template-columns: 1fr;
  }

  .section-header {
    margin-bottom: 48px;
  }
}
</style>
