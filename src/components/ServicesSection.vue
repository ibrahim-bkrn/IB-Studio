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
          :style="{ transitionDelay: `${i * 100}ms` }"
          role="listitem"
        >
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
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.1 })

const services = [
  {
    icon: '✦',
    title: 'Conception & Design',
    text: 'Une identité visuelle forte et cohérente, pensée pour marquer les esprits et renforcer la crédibilité de votre marque.',
  },
  {
    icon: '⚡',
    title: 'Développement sur-mesure',
    text: 'La technologie choisie selon votre projet — pas l\'inverse. WordPress, code natif, CRM, e-commerce ou plateforme communautaire.',
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
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1), transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.services-container.visible {
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

.service-card {
  background: #FFFFFF;
  border: 1px solid rgba(10, 15, 30, 0.07);
  border-radius: 20px;
  padding: 40px 36px;
  position: relative;
  overflow: hidden;
  cursor: default;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04), 0 4px 16px rgba(0, 0, 0, 0.04);
}

.service-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.03) 0%, transparent 60%);
  border-radius: 20px;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.service-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 40px rgba(37, 99, 235, 0.12), 0 2px 8px rgba(0, 0, 0, 0.06);
  border-color: rgba(37, 99, 235, 0.2);
}

.service-card:hover::before {
  opacity: 1;
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

.service-card:hover .card-icon {
  background: rgba(37, 99, 235, 0.15);
  transform: scale(1.05);
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

.service-card:hover .card-line {
  width: 100%;
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
