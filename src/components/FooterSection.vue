<template>
  <footer class="footer" role="contentinfo">
    <div class="footer-grid" aria-hidden="true"></div>
    <div class="footer-container">
      <div class="footer-top">
        <a href="#hero" class="footer-logo" aria-label="Retour en haut de page">
          <LogoBrand :height="26" />
        </a>
        <nav class="footer-nav" aria-label="Navigation footer">
          <a href="#services" class="footer-link">Services</a>
          <a href="#projet" class="footer-link">Mon approche</a>
          <a href="#contact" class="footer-link">Contact</a>
        </nav>
      </div>
      <div class="footer-divider" aria-hidden="true"></div>
      <div class="footer-bottom">
        <p class="footer-copy">© 2025 IB Studio — Tous droits réservés</p>
        <p class="footer-crafted">Conçu et développé avec soin.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import LogoBrand from './LogoBrand.vue'
</script>

<style scoped>
.footer {
  background: #060A16;
  padding: 60px 24px 40px;
  position: relative;
  overflow: hidden;
}

.footer-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.015) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.015) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
}

.footer-container {
  max-width: 1100px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.footer-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 32px;
  flex-wrap: wrap;
  gap: 20px;
}

.footer-logo {
  display: flex;
  align-items: center;
  transition: opacity 0.3s ease;
}

.footer-logo:hover {
  opacity: 0.75;
}

.footer-nav {
  display: flex;
  gap: 32px;
  flex-wrap: wrap;
}

.footer-link {
  font-size: 14px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.5);
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: #F8FAFC;
}

.footer-divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.08), transparent);
  margin-bottom: 28px;
}

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 8px;
}

.footer-copy {
  font-size: 13px;
  color: rgba(248, 250, 252, 0.35);
}

.footer-crafted {
  font-size: 13px;
  color: rgba(248, 250, 252, 0.35);
  font-style: italic;
}

@media (max-width: 768px) {
  .footer-top {
    flex-direction: column;
    align-items: flex-start;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 4px;
  }
}
</style>
