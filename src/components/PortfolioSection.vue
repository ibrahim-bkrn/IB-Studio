<template>
  <section class="portfolio" id="portfolio" aria-labelledby="portfolio-title">

    <!-- Teaser bridge depuis Services -->
    <div class="portfolio-bridge" ref="bridgeEl" :class="{ visible: bridgeVisible }">
      <div class="bridge-line" aria-hidden="true"></div>
      <p class="bridge-text">Vous voulez voir ce que ça donne ?</p>
      <div class="bridge-line" aria-hidden="true"></div>
    </div>

    <div class="portfolio-container">

      <div class="section-header" ref="headerEl" :class="{ visible: headerVisible }">
        <span class="section-label">✦ Réalisations</span>
        <h2 id="portfolio-title" class="section-title">Des sites qui parlent d'eux-mêmes</h2>
        <p class="section-subtitle">4 projets livrés — chacun avec une identité forte et un objectif précis.</p>

      </div>

      <!-- Carousel -->
      <div class="carousel-wrap" ref="wrapEl" :class="{ visible: wrapVisible }">

        <div class="carousel-track" ref="trackEl">

            <!-- Abou Zaynah -->
            <article class="p-card" @mouseenter="play('az')" @mouseleave="pause('az')">
              <div class="p-media">
                <div class="p-chrome">
                  <span class="dot dot--red"></span>
                  <span class="dot dot--yellow"></span>
                  <span class="dot dot--green"></span>
                  <span class="p-url">abuzaynah.com</span>
                </div>
                <div class="p-screen">
                  <img src="/portfolio/abuZaynah.jpeg" alt="Abou Zaynah" class="p-img" :class="{ hidden: active.az }" loading="lazy" />
                </div>
              </div>
              <div class="p-body">
                <div class="p-row">
                  <h3 class="p-name">Abou Zaynah</h3>
                  <a href="https://abuzaynah.com" target="_blank" rel="noopener noreferrer" class="p-link">Voir ↗</a>
                </div>
                <p class="p-desc">Miel artisanal premium — transmettre l'excellence et le savoir-faire à travers chaque détail visuel.</p>
                <div class="p-tags">
                  <span>E-commerce</span><span>Design premium</span><span>Sur-mesure</span>
                </div>
              </div>
            </article>

            <!-- La Hargne -->
            <article class="p-card" @mouseenter="play('lh')" @mouseleave="pause('lh')">
              <div class="p-media">
                <div class="p-chrome">
                  <span class="dot dot--red"></span>
                  <span class="dot dot--yellow"></span>
                  <span class="dot dot--green"></span>
                  <span class="p-url">lahargne.fr</span>
                </div>
                <div class="p-screen">
                  <img src="/portfolio/lahargne.png" alt="La Hargne" class="p-img" :class="{ hidden: active.lh }" loading="lazy" />
                </div>
              </div>
              <div class="p-body">
                <div class="p-row">
                  <h3 class="p-name">La Hargne</h3>
                  <a href="https://la-hargne.vercel.app" target="_blank" rel="noopener noreferrer" class="p-link">Voir ↗</a>
                </div>
                <p class="p-desc">Marque de t-shirts atypique — une identité brute et assumée qui ne laisse pas indifférent.</p>
                <div class="p-tags">
                  <span>E-commerce</span><span>Identité de marque</span><span>Sur-mesure</span>
                </div>
              </div>
            </article>

            <!-- Horizon -->
            <article class="p-card" @mouseenter="play('hz')" @mouseleave="pause('hz')">
              <div class="p-media">
                <div class="p-chrome">
                  <span class="dot dot--red"></span>
                  <span class="dot dot--yellow"></span>
                  <span class="dot dot--green"></span>
                  <span class="p-url">serriasecurite.com</span>
                </div>
                <div class="p-screen">
                  <img src="/public/portfolio/serria.png" alt="Serria Sécurité" class="p-img" :class="{ hidden: active.hz }" loading="lazy" />
                </div>
              </div>
              <div class="p-body">
                <div class="p-row">
                  <h3 class="p-name">Serria Sécurité</h3>
                  <a href="https://serriasecurite.vercel.app" target="_blank" rel="noopener noreferrer" class="p-link">Voir ↗</a>
                </div>
                <p class="p-desc">Site vitrine pour une entreprise de sécurité.</p>
                <div class="p-tags">
                  <span>Site vitrine</span><span>Refonte</span><span>Sur-mesure</span>
                </div>
              </div>
            </article>

            <!-- IB Studio -->
            <article class="p-card p-card--self">
              <div class="p-media">
                <div class="p-chrome">
                  <span class="dot dot--red"></span>
                  <span class="dot dot--yellow"></span>
                  <span class="dot dot--green"></span>
                  <span class="p-url">ib-studio.fr</span>
                </div>
                <div class="p-screen">
                  <img src="/og-image.png" alt="IB Studio" class="p-img p-img--og" loading="lazy" />
                </div>
              </div>
              <div class="p-body">
                <div class="p-row">
                  <h3 class="p-name">IB Studio <span class="p-badge">Ce site</span></h3>
                  <a href="https://ib-studio.fr" target="_blank" rel="noopener noreferrer" class="p-link">Voir ↗</a>
                </div>
                <p class="p-desc">Vitrine professionnelle avec animations avancées, design premium et performance optimisée.</p>
                <div class="p-tags">
                  <span>Site vitrine</span><span>Animations</span><span>Sur-mesure</span>
                </div>
              </div>
            </article>

            <!-- CTA card -->
            <article class="p-card p-card--cta">
              <div class="p-media">
                <div class="p-chrome">
                  <span class="dot dot--red"></span>
                  <span class="dot dot--yellow"></span>
                  <span class="dot dot--green"></span>
                  <span class="p-url p-url--placeholder">votre-site.fr</span>
                </div>
                <div class="p-screen p-screen--empty">
                  <div class="p-screen-plus" aria-hidden="true">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                      <line x1="12" y1="5" x2="12" y2="19"/>
                      <line x1="5" y1="12" x2="19" y2="12"/>
                    </svg>
                  </div>
                </div>
              </div>
              <div class="p-body">
                <div class="p-row">
                  <h3 class="p-name">Votre projet <span class="p-badge p-badge--next">À venir</span></h3>
                </div>
                <p class="p-desc">Et pourquoi le prochain ne serait pas vous ? Chaque projet ici a commencé par une conversation.</p>
                <a href="#contact" class="p-cta-btn">Démarrer mon projet →</a>
              </div>
            </article>

        </div>

        <!-- Arrows (desktop) -->
        <button class="carousel-arrow carousel-arrow--prev" @click="scroll(-1)" aria-label="Projet précédent">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M17 10a.75.75 0 0 1-.75.75H5.612l4.158 3.96a.75.75 0 1 1-1.04 1.08l-5.5-5.25a.75.75 0 0 1 0-1.08l5.5-5.25a.75.75 0 1 1 1.04 1.08L5.612 9.25H16.25A.75.75 0 0 1 17 10Z" clip-rule="evenodd" />
          </svg>
        </button>
        <button class="carousel-arrow carousel-arrow--next" @click="scroll(1)" aria-label="Projet suivant">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" style="transform: rotate(180deg)">
            <path fill-rule="evenodd" d="M17 10a.75.75 0 0 1-.75.75H5.612l4.158 3.96a.75.75 0 1 1-1.04 1.08l-5.5-5.25a.75.75 0 0 1 0-1.08l5.5-5.25a.75.75 0 1 1 1.04 1.08L5.612 9.25H16.25A.75.75 0 0 1 17 10Z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>

      <!-- Dots -->
      <div class="carousel-dots" :class="{ visible: wrapVisible }" role="tablist" aria-label="Projets">
        <button
          v-for="(_, i) in 5"
          :key="i"
          class="carousel-dot"
          :class="{ active: activeIndex === i }"
          @click="scrollTo(i)"
          :aria-label="`Projet ${i + 1}`"
          role="tab"
          :aria-selected="activeIndex === i"
        ></button>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted, nextTick } from 'vue'
import { useIntersection } from '../composables/useIntersection.js'

const { el: bridgeEl, isVisible: bridgeVisible } = useIntersection({ threshold: 0.3 })
const { el: headerEl, isVisible: headerVisible } = useIntersection({ threshold: 0.1 })
const { el: wrapEl, isVisible: wrapVisible } = useIntersection({ threshold: 0.05 })

const trackEl = ref(null)
const activeIndex = ref(0)

const azRef = ref(null)
const lhRef = ref(null)
const hzRef = ref(null)

const active = reactive({ az: false, lh: false, hz: false })
const videoRefs = { az: azRef, lh: lhRef, hz: hzRef }

function play(key) {
  const v = videoRefs[key]?.value
  if (!v) return
  v.play().catch(() => {})
  active[key] = true
}

function pause(key) {
  const v = videoRefs[key]?.value
  if (!v) return
  v.pause()
  v.currentTime = 0
  active[key] = false
}

function getCardWidth() {
  const track = trackEl.value
  if (!track) return 0
  const card = track.querySelector('.p-card')
  if (!card) return 0
  return card.offsetWidth + 20
}

function scroll(dir) {
  const track = trackEl.value
  if (!track) return
  track.scrollBy({ left: dir * getCardWidth(), behavior: 'smooth' })
}

function scrollTo(i) {
  const track = trackEl.value
  if (!track) return
  track.scrollTo({ left: i * getCardWidth(), behavior: 'smooth' })
}

function onTrackScroll() {
  const track = trackEl.value
  if (!track) return
  const cardW = getCardWidth()
  if (cardW === 0) return
  activeIndex.value = Math.round(track.scrollLeft / cardW)
}

onMounted(() => {
  const isMobile = window.matchMedia('(hover: none)').matches
  if (isMobile) {
    nextTick(() => {
      Object.keys(videoRefs).forEach(key => play(key))
    })
  }
  trackEl.value?.addEventListener('scroll', onTrackScroll, { passive: true })
})

onUnmounted(() => {
  trackEl.value?.removeEventListener('scroll', onTrackScroll)
})
</script>

<style scoped>
/* ── Section ── */
.portfolio {
  background: #0A0F1E;
}

/* ── Bridge ── */
.portfolio-bridge {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 56px 24px 0;
  max-width: 860px;
  margin: 0 auto;
  opacity: 0;
  transform: translateY(16px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.portfolio-bridge.visible {
  opacity: 1;
  transform: translateY(0);
}

.bridge-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.08), transparent);
}

.bridge-text {
  font-size: 15px;
  font-weight: 500;
  color: rgba(248, 250, 252, 0.3);
  white-space: nowrap;
  font-style: italic;
  letter-spacing: 0.2px;
}

/* ── Container ── */
.portfolio-container {
  padding: 64px 0 100px;
}

/* ── Header ── */
.section-header {
  text-align: center;
  margin-bottom: 56px;
  padding: 0 24px;
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.section-header.visible { opacity: 1; transform: translateY(0); }

.section-label {
  display: block;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #2563EB;
  margin-bottom: 16px;
}

.section-title {
  font-size: clamp(28px, 4vw, 44px);
  font-weight: 800;
  letter-spacing: -1.5px;
  color: #F8FAFC;
  line-height: 1.1;
  margin-bottom: 12px;
}

.section-subtitle {
  font-size: 16px;
  color: rgba(248, 250, 252, 0.4);
  max-width: 380px;
  margin: 0 auto;
  line-height: 1.7;
  font-style: italic;
}

/* ── Carousel wrap ── */
.carousel-wrap {
  position: relative;
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease 0.1s, transform 0.6s ease 0.1s;
}
.carousel-wrap.visible { opacity: 1; transform: translateY(0); }

/* ── Fade bords (pseudo-éléments, desktop) ── */
@media (hover: hover) {
  .carousel-wrap::before,
  .carousel-wrap::after {
    content: '';
    position: absolute;
    top: 0;
    bottom: 20px;
    width: 80px;
    z-index: 1;
    pointer-events: none;
  }
  .carousel-wrap::before {
    left: 0;
    background: linear-gradient(90deg, #0A0F1E 0%, transparent 100%);
  }
  .carousel-wrap::after {
    right: 0;
    background: linear-gradient(90deg, transparent 0%, #0A0F1E 100%);
  }
}

/* ── Track ── */
.carousel-track {
  display: flex;
  gap: 20px;
  padding: 8px 24px 20px;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scrollbar-width: none;
  -webkit-overflow-scrolling: touch;
}
.carousel-track::-webkit-scrollbar { display: none; }

/* ── Cards ── */
.p-card {
  flex-shrink: 0;
  width: 500px;
  scroll-snap-align: start;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 20px;
  overflow: hidden;
  transition: border-color 0.3s ease, box-shadow 0.3s ease, transform 0.3s ease;
}

@media (hover: hover) {
  .p-card:hover {
    border-color: rgba(37, 99, 235, 0.4);
    box-shadow: 0 20px 48px rgba(0, 0, 0, 0.5);
    transform: translateY(-4px);
  }
}

/* Browser chrome */
.p-chrome {
  display: flex;
  align-items: center;
  gap: 5px;
  padding: 9px 14px;
  background: rgba(255, 255, 255, 0.03);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  flex-shrink: 0;
}
.dot--red    { background: rgba(239, 68, 68, 0.55); }
.dot--yellow { background: rgba(234, 179, 8, 0.55); }
.dot--green  { background: rgba(34, 197, 94, 0.55); }

.p-url {
  margin-left: 8px;
  font-size: 11px;
  color: rgba(255, 255, 255, 0.28);
  background: rgba(255, 255, 255, 0.05);
  padding: 2px 10px;
  border-radius: 20px;
  font-family: monospace;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* Screen */
.p-screen {
  position: relative;
  aspect-ratio: 16 / 9;
  overflow: hidden;
  background: #060A14;
}

.p-img,
.p-vid {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top center;
  transition: opacity 0.4s ease;
}

.p-img.hidden  { opacity: 0; }
.p-vid         { opacity: 0; }
.p-vid.show    { opacity: 1; }

.p-img--og {
  object-position: center center;
}

/* Card body */
.p-body {
  padding: 18px 20px 22px;
}

.p-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
  gap: 8px;
}

.p-name {
  font-size: 17px;
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -0.3px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.p-badge {
  font-size: 10px;
  font-weight: 600;
  color: #60A5FA;
  background: rgba(37, 99, 235, 0.15);
  border: 1px solid rgba(37, 99, 235, 0.25);
  padding: 2px 8px;
  border-radius: 50px;
}

.p-link {
  font-size: 12px;
  font-weight: 600;
  color: rgba(96, 165, 250, 0.7);
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;
  transition: color 0.2s ease;
}
@media (hover: hover) {
  .p-link:hover { color: #93C5FD; }
}

.p-desc {
  font-size: 13px;
  color: rgba(248, 250, 252, 0.42);
  line-height: 1.65;
  margin-bottom: 14px;
}

.p-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.p-tags span {
  font-size: 11px;
  font-weight: 600;
  color: rgba(96, 165, 250, 0.75);
  background: rgba(37, 99, 235, 0.1);
  border: 1px solid rgba(37, 99, 235, 0.18);
  padding: 3px 10px;
  border-radius: 50px;
}

/* ── CTA card ── */
.p-card--cta {
  border-style: dashed;
  border-color: rgba(37, 99, 235, 0.25);
  background: rgba(37, 99, 235, 0.03);
}

@media (hover: hover) {
  .p-card--cta:hover {
    border-color: rgba(37, 99, 235, 0.5);
    box-shadow: 0 20px 48px rgba(37, 99, 235, 0.15);
    transform: translateY(-4px);
  }
}

.p-url--placeholder {
  color: rgba(96, 165, 250, 0.4);
  font-style: italic;
}

.p-screen--empty {
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(37, 99, 235, 0.04);
  border: 1.5px dashed rgba(37, 99, 235, 0.18);
  border-radius: 0;
}

.p-screen-plus {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  border: 1.5px dashed rgba(37, 99, 235, 0.35);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(37, 99, 235, 0.5);
  transition: border-color 0.3s ease, color 0.3s ease, transform 0.3s ease;
}

.p-screen-plus svg {
  width: 20px;
  height: 20px;
}

@media (hover: hover) {
  .p-card--cta:hover .p-screen-plus {
    border-color: rgba(37, 99, 235, 0.7);
    color: rgba(96, 165, 250, 0.8);
    transform: scale(1.1);
  }
}

.p-badge--next {
  color: rgba(96, 165, 250, 0.9);
  background: rgba(37, 99, 235, 0.12);
  border-color: rgba(37, 99, 235, 0.2);
}

.p-cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 10px 20px;
  background: #2563EB;
  color: #fff;
  font-size: 13px;
  font-weight: 600;
  border-radius: 50px;
  text-decoration: none;
  transition: background 0.2s ease, box-shadow 0.2s ease, transform 0.2s ease;
  margin-top: 6px;
}

@media (hover: hover) {
  .p-cta-btn:hover {
    background: #1D4ED8;
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
    transform: translateY(-1px);
  }
}

/* ── Arrows ── */
.carousel-arrow {
  position: absolute;
  top: 42%;
  transform: translateY(-50%);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.07);
  border: 1px solid rgba(255, 255, 255, 0.12);
  cursor: pointer;
  color: rgba(255, 255, 255, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  z-index: 2;
}

.carousel-arrow svg {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
}

.carousel-arrow--prev { left: 16px; }
.carousel-arrow--next { right: 16px; }

@media (hover: hover) {
  .carousel-arrow:hover {
    background: #2563EB;
    border-color: #2563EB;
    color: #fff;
    box-shadow: 0 4px 20px rgba(37, 99, 235, 0.4);
  }
}

/* ── Dots ── */
.carousel-dots {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin-top: 24px;
  opacity: 0;
  transition: opacity 0.6s ease 0.3s;
}
.carousel-dots.visible { opacity: 1; }

.carousel-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  padding: 0;
}

.carousel-dot.active {
  width: 24px;
  border-radius: 4px;
  background: #2563EB;
}

/* ── Responsive ── */
@media (max-width: 768px) {
  .carousel-fade {
    -webkit-mask-image: none;
    mask-image: none;
  }

  .carousel-track {
    padding: 8px 20px 20px;
    gap: 16px;
  }

  .p-card {
    width: calc(100vw - 48px);
  }

  .carousel-arrow {
    display: none;
  }

  .portfolio-container {
    padding: 48px 0 80px;
  }

  .section-header {
    margin-bottom: 40px;
  }
}
</style>
