<template>
  <section class="portfolio" aria-labelledby="portfolio-title">
    <div ref="sectionEl" class="portfolio-container" :class="{ visible: isVisible }">

      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Réalisations</span>
        <h2 id="portfolio-title" class="section-title">Ce que j'ai construit</h2>
        <p class="section-subtitle">
          Chaque ligne de code sur ce site est une preuve de ce que je peux livrer.
        </p>
      </div>

      <div class="portfolio-grid">

        <!-- Projet 1 : ibstudio.fr -->
        <article class="portfolio-card portfolio-card--main">
          <div class="card-browser">
            <div class="browser-bar">
              <span class="browser-dot"></span>
              <span class="browser-dot"></span>
              <span class="browser-dot"></span>
              <div class="browser-url">ibstudio.fr</div>
            </div>
            <div class="browser-preview">
              <div class="preview-hero">
                <div class="preview-badge"></div>
                <div class="preview-title"></div>
                <div class="preview-title preview-title--short"></div>
                <div class="preview-buttons">
                  <div class="preview-btn preview-btn--primary"></div>
                  <div class="preview-btn preview-btn--secondary"></div>
                </div>
              </div>
              <div class="preview-orb preview-orb--1"></div>
              <div class="preview-orb preview-orb--2"></div>
            </div>
          </div>

          <div class="card-body">
            <div class="card-meta">
              <span class="card-status">
                <span class="status-dot" aria-hidden="true"></span>
                En ligne
              </span>
              <span class="card-year">2025</span>
            </div>
            <h3 class="card-title">IB Studio — Site vitrine</h3>
            <p class="card-text">
              Ce site. Design sur-mesure, animations fluides, expérience mobile
              soignée, chargement rapide, SEO technique intégré, déployé sur Vercel.
              Une vitrine pensée pour convaincre — pas juste pour exister.
            </p>
            <div class="card-tags" aria-label="Caractéristiques">
              <span>Design sur-mesure</span>
              <span>Responsive</span>
              <span>SEO</span>
              <span>Rapide</span>
              <span>Vercel</span>
            </div>
          </div>
        </article>

        <!-- Placeholder : à venir -->
        <article class="portfolio-card portfolio-card--soon" aria-label="Prochain projet">
          <div class="soon-content">
            <div class="soon-icon" aria-hidden="true">◌</div>
            <h3 class="soon-title">Votre projet ici</h3>
            <p class="soon-text">
              Je suis en phase de lancement. Les premiers clients bénéficient
              d'une attention maximale et de conditions préférentielles.
            </p>
            <a href="#contact" class="soon-cta">
              Discutons de votre projet
              <span aria-hidden="true">→</span>
            </a>
          </div>
          <div class="soon-bg-text" aria-hidden="true">02</div>
        </article>

      </div>
    </div>
  </section>
</template>

<script setup>
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.08 })
</script>

<style scoped>
.portfolio {
  background: #F8FAFC;
  padding: 120px 24px;
  position: relative;
}

.portfolio::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 800px;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.25), transparent);
}

.portfolio-container {
  max-width: 1100px;
  margin: 0 auto;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1),
              transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.portfolio-container.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Header */
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

.portfolio-container.visible .section-title::after {
  width: 60px;
}

.section-subtitle {
  font-size: 17px;
  color: #64748B;
  font-style: italic;
  line-height: 1.7;
}

/* Grid */
.portfolio-grid {
  display: grid;
  grid-template-columns: 1fr 380px;
  gap: 24px;
  align-items: stretch;
}

/* ── Carte principale ── */
.portfolio-card {
  border-radius: 24px;
  overflow: hidden;
}

.portfolio-card--main {
  background: #FFFFFF;
  border: 1px solid rgba(10, 15, 30, 0.08);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.06);
  transition: box-shadow 0.3s ease, border-color 0.3s ease;
}

@media (hover: hover) {
  .portfolio-card--main:hover {
    box-shadow: 0 8px 48px rgba(37, 99, 235, 0.1), 0 2px 8px rgba(0, 0, 0, 0.06);
    border-color: rgba(37, 99, 235, 0.18);
  }
}

/* Browser mockup */
.card-browser {
  background: #0A0F1E;
  border-radius: 24px 24px 0 0;
}

.browser-bar {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 12px 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.browser-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.12);
}

.browser-dot:nth-child(1) { background: rgba(239, 68, 68, 0.6); }
.browser-dot:nth-child(2) { background: rgba(234, 179, 8, 0.6); }
.browser-dot:nth-child(3) { background: rgba(34, 197, 94, 0.6); }

.browser-url {
  margin-left: 12px;
  font-size: 11px;
  color: rgba(255, 255, 255, 0.35);
  background: rgba(255, 255, 255, 0.06);
  padding: 3px 12px;
  border-radius: 50px;
  font-family: monospace;
  letter-spacing: 0.3px;
}

/* Preview screen */
.browser-preview {
  height: 180px;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 24px;
}

.preview-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(40px);
  pointer-events: none;
}

.preview-orb--1 {
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.35) 0%, transparent 70%);
  top: -60px;
  left: -40px;
}

.preview-orb--2 {
  width: 160px;
  height: 160px;
  background: radial-gradient(circle, rgba(139, 92, 246, 0.2) 0%, transparent 70%);
  bottom: -40px;
  right: -20px;
}

.preview-hero {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  width: 100%;
}

.preview-badge {
  width: 120px;
  height: 10px;
  background: rgba(96, 165, 250, 0.25);
  border-radius: 50px;
  border: 1px solid rgba(96, 165, 250, 0.2);
}

.preview-title {
  width: 260px;
  height: 14px;
  background: rgba(248, 250, 252, 0.18);
  border-radius: 4px;
}

.preview-title--short {
  width: 200px;
  height: 14px;
  background: rgba(248, 250, 252, 0.1);
}

.preview-buttons {
  display: flex;
  gap: 8px;
  margin-top: 4px;
}

.preview-btn {
  height: 22px;
  border-radius: 50px;
}

.preview-btn--primary {
  width: 90px;
  background: rgba(37, 99, 235, 0.7);
}

.preview-btn--secondary {
  width: 70px;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.12);
}

/* Card body */
.card-body {
  padding: 28px 32px 32px;
}

.card-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 14px;
}

.card-status {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  font-weight: 600;
  color: #10B981;
}

.status-dot {
  width: 7px;
  height: 7px;
  background: #10B981;
  border-radius: 50%;
  animation: status-pulse 2s ease-in-out infinite;
}

@keyframes status-pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.4); }
  50%       { box-shadow: 0 0 0 5px rgba(16, 185, 129, 0); }
}

.card-year {
  font-size: 12px;
  color: #94A3B8;
  font-weight: 500;
}

.card-title {
  font-size: 22px;
  font-weight: 700;
  color: #0A0F1E;
  letter-spacing: -0.5px;
  margin-bottom: 10px;
}

.card-text {
  font-size: 14.5px;
  color: #64748B;
  line-height: 1.75;
  margin-bottom: 20px;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.card-tags span {
  font-size: 12px;
  font-weight: 600;
  color: #2563EB;
  background: rgba(37, 99, 235, 0.08);
  border: 1px solid rgba(37, 99, 235, 0.15);
  padding: 4px 12px;
  border-radius: 50px;
}

/* ── Carte "à venir" ── */
.portfolio-card--soon {
  background: #0A0F1E;
  border: 1px solid rgba(37, 99, 235, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: 48px 36px;
  transition: border-color 0.3s ease;
}

@media (hover: hover) {
  .portfolio-card--soon:hover {
    border-color: rgba(37, 99, 235, 0.4);
  }
  .portfolio-card--soon:hover .soon-cta {
    background: #1d4ed8;
    box-shadow: 0 0 20px rgba(37, 99, 235, 0.4);
  }
}

.soon-content {
  position: relative;
  z-index: 1;
  text-align: center;
}

.soon-bg-text {
  position: absolute;
  bottom: -20px;
  right: -10px;
  font-size: 120px;
  font-weight: 800;
  color: rgba(37, 99, 235, 0.04);
  letter-spacing: -8px;
  line-height: 1;
  pointer-events: none;
  user-select: none;
}

.soon-icon {
  font-size: 40px;
  color: rgba(96, 165, 250, 0.4);
  margin-bottom: 20px;
  animation: soon-pulse 3s ease-in-out infinite;
}

@keyframes soon-pulse {
  0%, 100% { opacity: 0.4; }
  50%       { opacity: 0.8; }
}

.soon-title {
  font-size: 22px;
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -0.5px;
  margin-bottom: 12px;
}

.soon-text {
  font-size: 14px;
  color: rgba(248, 250, 252, 0.45);
  line-height: 1.75;
  margin-bottom: 28px;
}

.soon-cta {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 13px 24px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Responsive */
@media (max-width: 1024px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }

  .portfolio-card--soon {
    min-height: 260px;
  }
}

@media (max-width: 768px) {
  .portfolio {
    padding: 80px 20px;
  }

  .section-header {
    margin-bottom: 48px;
  }

  .card-body {
    padding: 24px 24px 28px;
  }
}
</style>
