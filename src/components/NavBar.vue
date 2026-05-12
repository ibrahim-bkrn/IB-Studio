<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }" role="navigation" aria-label="Navigation principale">
    <div class="nav-container">
      <a href="#hero" class="nav-logo" aria-label="Retour en haut">
        <LogoBrand :height="isScrolled ? 22 : 28" />
      </a>

      <ul class="nav-links" role="list">
        <li v-for="link in links" :key="link.href">
          <a
            :href="link.href"
            class="nav-link"
            :class="{ active: activeSection === link.section }"
          >{{ link.label }}</a>
        </li>
      </ul>

      <a href="#contact" class="nav-cta" aria-label="Discuter de votre projet">
        Parlons de votre projet
      </a>

    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import LogoBrand from './LogoBrand.vue'

const isScrolled = ref(false)
const activeSection = ref('hero')

const links = [
  { href: '#services', label: 'Services', section: 'services' },
  { href: '#processus', label: 'Processus', section: 'processus' },
  { href: '#projet', label: 'Projets', section: 'projet' },
  { href: '#faq', label: 'FAQ', section: 'faq' },
  { href: '#contact', label: 'Contact', section: 'contact' },
]

function onScroll() {
  isScrolled.value = window.scrollY > 40

  const sections = ['hero', 'services', 'processus', 'projet', 'faq', 'contact']
  for (const id of sections) {
    const el = document.getElementById(id)
    if (!el) continue
    const rect = el.getBoundingClientRect()
    if (rect.top <= 80 && rect.bottom > 80) {
      activeSection.value = id
      break
    }
  }
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 20px 0;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar.scrolled {
  background: rgba(10, 15, 30, 0.85);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  padding: 10px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.3);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
}

.nav-logo {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  transition: opacity 0.3s ease;
}

.nav-logo:hover {
  opacity: 0.8;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 36px;
  list-style: none;
}

.nav-link {
  font-size: 15px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.7);
  transition: color 0.3s ease;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: #2563EB;
  border-radius: 2px;
  transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-link:hover,
.nav-link.active {
  color: #F8FAFC;
}

.nav-link:hover::after,
.nav-link.active::after {
  width: 100%;
}

.nav-cta {
  font-size: 14px;
  font-weight: 600;
  color: #F8FAFC;
  background: #2563EB;
  padding: 10px 20px;
  border-radius: 50px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  flex-shrink: 0;
  box-shadow: 0 0 0 0 rgba(37, 99, 235, 0.4);
  display: flex;
  align-items: center;
  gap: 6px;
}

.nav-cta:hover {
  transform: scale(1.03);
  box-shadow: 0 0 24px rgba(37, 99, 235, 0.6);
  background: #1d4ed8;
}

@media (max-width: 768px) {
  .nav-container {
    gap: 0;
  }

  .nav-links {
    display: none;
  }

  .nav-cta {
    display: none;
  }
}
</style>
