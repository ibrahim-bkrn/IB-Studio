<template>
  <section class="about" id="apropos" aria-label="À propos">
    <div class="about-container">

      <div class="about-right" ref="el" :class="{ visible: isVisible }">
        <p class="section-eyebrow">À propos</p>
        <h2 class="about-title">
          Créateur de sites web freelance,<br />
          <span class="about-grad">entrepreneur comme vous.</span>
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
  background: #0A0F1E;
  padding: 120px 24px;
}

.about-container {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

/* ── Contenu, centré ── */
.about-right {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease, transform 0.6s ease;
  text-align: center;
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
  color: #F8FAFC;
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
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.75;
  margin-bottom: 18px;
}

.about-values {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin: 32px auto 36px;
  max-width: 440px;
  text-align: left;
}

.about-values li {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.value-icon {
  width: 40px;
  height: 40px;
  background: rgba(37, 99, 235, 0.1);
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
  color: #F8FAFC;
  margin-bottom: 2px;
}

.value-sub {
  font-size: 13px;
  color: rgba(248, 250, 252, 0.45);
  font-weight: 400;
}

.about-cta {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.2s ease;
  letter-spacing: -0.2px;
}

.about-cta:hover {
  background: #1d4ed8;
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

  .about-title {
    font-size: 28px;
  }
}
</style>
