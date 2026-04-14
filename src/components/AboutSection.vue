<template>
  <section class="about" id="apropos" aria-label="À propos">
    <div class="about-container">

      <div class="about-left" ref="el" :class="{ visible: isVisible }">
        <div class="about-avatar" aria-hidden="true">
          <span class="avatar-initials">IB</span>
          <div class="avatar-ring"></div>
          <div class="avatar-dot"></div>
        </div>
      </div>

      <div class="about-right" :class="{ visible: isVisible }">
        <p class="section-eyebrow">À propos</p>
        <h2 class="about-title">
          Créateur de sites web freelance,<br />
          <span class="about-grad">votre réussite en ligne, c'est mon objectif.</span>
        </h2>
        <p class="about-text">
          Issu d'une grande école d'ingénieurs du numérique, je crée des sites web pour les entrepreneurs, artisans et PME qui veulent une présence en ligne à la hauteur de leur ambition — sans se noyer dans des agences coûteuses ou des outils qui ne leur conviennent pas.
        </p>
        <p class="about-text">
          Mon approche : comprendre votre métier avant de construire quoi que ce soit. Je choisis l'outil adapté — WordPress, CMS ou solution sur-mesure — selon votre projet, votre budget et vos objectifs.
        </p>

        <ul class="about-values" role="list">
          <li>
            <div class="value-icon">🎓</div>
            <div>
              <div class="value-title">Formation d'ingénieur</div>
              <div class="value-sub">Grande école du numérique — rigueur et méthode</div>
            </div>
          </li>
          <li>
            <div class="value-icon">⚡</div>
            <div>
              <div class="value-title">Livraison rapide</div>
              <div class="value-sub">Résultats concrets, sans délais interminables</div>
            </div>
          </li>
          <li>
            <div class="value-icon">🤝</div>
            <div>
              <div class="value-title">Un seul interlocuteur</div>
              <div class="value-sub">Vous me parlez directement, pas à une agence</div>
            </div>
          </li>
        </ul>

        <a href="#contact" class="about-cta">
          Travaillons ensemble
          <span aria-hidden="true">→</span>
        </a>
      </div>

    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'
const { el, isVisible } = useIntersection()
</script>

<style scoped>
.about {
  background: #F8FAFC;
  padding: 120px 24px;
}

.about-container {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 80px;
  align-items: start;
}

/* ── Avatar colonne gauche ── */
.about-left {
  opacity: 0;
  transform: translateX(-24px);
  transition: opacity 0.6s ease, transform 0.6s ease;
  display: flex;
  justify-content: center;
  padding-top: 12px;
}
.about-left.visible {
  opacity: 1;
  transform: translateX(0);
}

.about-avatar {
  position: relative;
  width: 200px;
  height: 200px;
}

.avatar-initials {
  width: 200px;
  height: 200px;
  border-radius: 24px;
  background: linear-gradient(135deg, #0A0F1E 0%, #1e3a8a 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 56px;
  font-weight: 800;
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
  background: linear-gradient(135deg, #2563EB, #60A5FA);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: absolute;
  inset: 0;
  /* override: show on bg */
  background-color: #0F172A;
  -webkit-text-fill-color: unset;
  color: #2563EB;
  letter-spacing: -2px;
  border: 1px solid rgba(37, 99, 235, 0.2);
  box-shadow: 0 20px 60px rgba(37, 99, 235, 0.15);
}

.avatar-ring {
  position: absolute;
  inset: -10px;
  border-radius: 32px;
  border: 1px solid rgba(37, 99, 235, 0.15);
  animation: ring-pulse 3s ease-in-out infinite;
}

@keyframes ring-pulse {
  0%, 100% { opacity: 0.4; transform: scale(1); }
  50% { opacity: 0.9; transform: scale(1.02); }
}

.avatar-dot {
  position: absolute;
  bottom: 8px;
  right: -4px;
  width: 18px;
  height: 18px;
  background: #10B981;
  border-radius: 50%;
  border: 3px solid #F8FAFC;
}

/* ── Contenu colonne droite ── */
.about-right {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease 0.15s, transform 0.6s ease 0.15s;
}
.about-right.visible {
  opacity: 1;
  transform: translateY(0);
}

.section-eyebrow {
  font-size: 12px;
  font-weight: 700;
  color: #2563EB;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.about-title {
  font-size: clamp(30px, 4vw, 42px);
  font-weight: 800;
  color: #0A0F1E;
  line-height: 1.15;
  letter-spacing: -1.5px;
  margin-bottom: 28px;
}

.about-grad {
  background: linear-gradient(135deg, #2563EB, #60A5FA);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.about-text {
  font-size: 16px;
  color: #475569;
  line-height: 1.75;
  margin-bottom: 18px;
}

.about-values {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin: 32px 0 36px;
}

.about-values li {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.value-icon {
  width: 40px;
  height: 40px;
  background: #EFF6FF;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}

.value-title {
  font-size: 14px;
  font-weight: 700;
  color: #0F172A;
  margin-bottom: 2px;
}

.value-sub {
  font-size: 13px;
  color: #94A3B8;
  font-weight: 400;
}

.about-cta {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  background: #0A0F1E;
  color: #F8FAFC;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.2s ease;
  letter-spacing: -0.2px;
}

.about-cta:hover {
  background: #2563EB;
  transform: translateY(-1px);
  box-shadow: 0 8px 24px rgba(37, 99, 235, 0.3);
}

.about-cta:active {
  transform: scale(0.97);
  transition-duration: 80ms;
}

/* ── Responsive ── */
@media (max-width: 768px) {
  .about {
    padding: 80px 20px;
  }

  .about-container {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .about-left {
    transform: translateY(-16px);
    justify-content: flex-start;
  }
  .about-left.visible {
    transform: translateY(0);
  }

  .about-avatar {
    width: 140px;
    height: 140px;
  }

  .avatar-initials {
    width: 140px;
    height: 140px;
    font-size: 40px;
  }

  .about-title {
    font-size: 28px;
  }
}
</style>
