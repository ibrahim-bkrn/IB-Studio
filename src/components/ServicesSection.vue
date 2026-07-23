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
          <div class="card-icon" aria-hidden="true" v-html="service.icon"></div>
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
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
  <path fill-rule="evenodd" d="M2.25 5.25a3 3 0 0 1 3-3h13.5a3 3 0 0 1 3 3V15a3 3 0 0 1-3 3h-3v.257c0 .597.237 1.17.659 1.591l.621.622a.75.75 0 0 1-.53 1.28h-9a.75.75 0 0 1-.53-1.28l.621-.622a2.25 2.25 0 0 0 .659-1.59V18h-3a3 3 0 0 1-3-3V5.25Zm1.5 0v7.5a1.5 1.5 0 0 0 1.5 1.5h13.5a1.5 1.5 0 0 0 1.5-1.5v-7.5a1.5 1.5 0 0 0-1.5-1.5H5.25a1.5 1.5 0 0 0-1.5 1.5Z" clip-rule="evenodd" />
</svg>`,
    title: 'Conception & Design',
    text: 'Une identité visuelle forte et cohérente, pensée pour marquer les esprits et renforcer la crédibilité de votre marque.',
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
  <path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5" />
</svg>`,
    title: 'Réalisation sur-mesure',
    text: 'L\'outil choisi selon votre projet — pas l\'inverse. WordPress, CMS, e-commerce ou solution spécifique : ce qui correspond à votre besoin et votre budget.',
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
  <path d="M4.5 3.75a3 3 0 0 0-3 3v.75h21v-.75a3 3 0 0 0-3-3h-15Z" />
  <path fill-rule="evenodd" d="M22.5 9.75h-21v7.5a3 3 0 0 0 3 3h15a3 3 0 0 0 3-3v-7.5Zm-18 3.75a.75.75 0 0 1 .75-.75h6a.75.75 0 0 1 0 1.5h-6a.75.75 0 0 1-.75-.75Zm.75 2.25a.75.75 0 0 0 0 1.5h3a.75.75 0 0 0 0-1.5h-3Z" clip-rule="evenodd" />
</svg>`,
    title: 'Référencement SEO',
    text: 'Pour être trouvé par vos clients, pas seulement visible. Une stratégie de référencement intégrée dès la conception.',
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
  <path fill-rule="evenodd" d="M12 6.75a5.25 5.25 0 0 1 6.775-5.025.75.75 0 0 1 .313 1.248l-3.32 3.319c.063.475.276.934.641 1.299.365.365.824.578 1.3.64l3.318-3.319a.75.75 0 0 1 1.248.313 5.25 5.25 0 0 1-5.472 6.756c-1.018-.086-1.87.1-2.309.634L7.344 21.3A3.298 3.298 0 1 1 2.7 16.657l8.684-7.151c.533-.44.72-1.291.634-2.309A5.342 5.342 0 0 1 12 6.75ZM4.117 19.125a.75.75 0 0 1 .75-.75h.008a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-.75.75h-.008a.75.75 0 0 1-.75-.75v-.008Z" clip-rule="evenodd" />
  <path d="m10.076 8.64-2.201-2.2V4.874a.75.75 0 0 0-.364-.643l-3.75-2.25a.75.75 0 0 0-.916.113l-.75.75a.75.75 0 0 0-.113.916l2.25 3.75a.75.75 0 0 0 .643.364h1.564l2.062 2.062 1.575-1.297Z" />
  <path fill-rule="evenodd" d="m12.556 17.329 4.183 4.182a3.375 3.375 0 0 0 4.773-4.773l-3.306-3.305a6.803 6.803 0 0 1-1.53.043c-.394-.034-.682-.006-.867.042a.589.589 0 0 0-.167.063l-3.086 3.748Zm3.414-1.36a.75.75 0 0 1 1.06 0l1.875 1.876a.75.75 0 1 1-1.06 1.06L15.97 17.03a.75.75 0 0 1 0-1.06Z" clip-rule="evenodd" />
</svg>`,
    title: 'Suivi & Maintenance',
    text: 'Je reste disponible après la livraison. Mises à jour, évolutions, support — votre site grandit avec votre business.',
  },
]
</script>

<style scoped>
.services {
  background: #0A0F1E;
  padding: 120px 24px;
  position: relative;
}

.services-container {
  max-width: 1100px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
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
  color: #F8FAFC;
  letter-spacing: -1.5px;
  margin-bottom: 16px;
  position: relative;
  display: inline-block;
}

.section-subtitle {
  font-size: 17px;
  color: rgba(248, 250, 252, 0.5);
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
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  padding: 40px 36px;
  position: relative;
  overflow: hidden;
  cursor: default;
  transition: box-shadow 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              border-color 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.1s ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2), 0 4px 16px rgba(0, 0, 0, 0.2);
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
    box-shadow: 0 8px 40px rgba(37, 99, 235, 0.2), 0 2px 8px rgba(0, 0, 0, 0.3);
    border-color: rgba(37, 99, 235, 0.4);
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
  color: rgba(255, 255, 255, 0.05);
  letter-spacing: -5px;
  line-height: 1;
  pointer-events: none;
  user-select: none;
  transition: color 0.3s ease;
  font-variant-numeric: tabular-nums;
}

.card-icon {
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

.card-icon :deep(svg) {
  width: 20px;
  height: 20px;
  flex-shrink: 0;
}

.card-title {
  font-size: 20px;
  font-weight: 700;
  color: #F8FAFC;
  margin-bottom: 12px;
  letter-spacing: -0.5px;
}

.card-text {
  font-size: 15px;
  color: rgba(248, 250, 252, 0.5);
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
