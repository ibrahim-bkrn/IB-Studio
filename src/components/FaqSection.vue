<template>
  <section class="faq" aria-labelledby="faq-title">
    <div ref="sectionEl" class="faq-container" :class="{ visible: isVisible }">
      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Questions fréquentes</span>
        <h2 id="faq-title" class="section-title">Tout ce que vous<br />voulez savoir.</h2>
        <p class="section-subtitle">
          Si votre question n'est pas là,
          <a href="#contact" class="subtitle-link">posez-la moi directement.</a>
        </p>
      </div>

      <div class="faq-grid">
        <div class="faq-list" role="list">
          <div
            v-for="(item, i) in faqs"
            :key="i"
            class="faq-item"
            :class="{ open: openIndex === i }"
            role="listitem"
          >
            <button
              class="faq-question"
              :aria-expanded="openIndex === i"
              :aria-controls="`faq-answer-${i}`"
              @click="toggle(i)"
            >
              <span>{{ item.question }}</span>
              <span class="faq-icon" aria-hidden="true">
                <svg
                  width="18"
                  height="18"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="m6 9 6 6 6-6" />
                </svg>
              </span>
            </button>

            <div
              :id="`faq-answer-${i}`"
              class="faq-answer"
              :style="{ maxHeight: openIndex === i ? answerHeight(i) : '0px' }"
              role="region"
              :aria-hidden="openIndex !== i"
            >
              <div class="faq-answer-inner" :ref="el => setAnswerRef(el, i)">
                <p>{{ item.answer }}</p>
              </div>
            </div>
          </div>
        </div>

        <aside class="faq-aside" aria-label="Invitation au contact">
          <div class="faq-cta-card">
            <div class="cta-icon" aria-hidden="true" style="width: 25px;">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="size-6">
                <path fill-rule="evenodd" d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12Zm11.378-3.917c-.89-.777-2.366-.777-3.255 0a.75.75 0 0 1-.988-1.129c1.454-1.272 3.776-1.272 5.23 0 1.513 1.324 1.513 3.518 0 4.842a3.75 3.75 0 0 1-.837.552c-.676.328-1.028.774-1.028 1.152v.75a.75.75 0 0 1-1.5 0v-.75c0-1.279 1.06-2.107 1.875-2.502.182-.088.351-.199.503-.331.83-.727.83-1.857 0-2.584ZM12 18a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Z" clip-rule="evenodd" />
              </svg>
            </div>
            <h3>Votre question n'est pas là ?</h3>
            <p>Je réponds à chaque message personnellement, sous 24h.</p>
            <a href="#contact" class="faq-cta-btn">
              Me poser une question
              <span aria-hidden="true">→</span>
            </a>
          </div>

          <div class="faq-stats">
            <div class="stat">
              <strong>24h</strong>
              <span>Délai de réponse max</span>
            </div>
            <div class="stat">
              <strong>100%</strong>
              <span>Réponses personnalisées</span>
            </div>
          </div>
        </aside>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.08 })

const openIndex = ref(0)
const answerRefs = ref([])

function setAnswerRef(el, i) {
  if (el) answerRefs.value[i] = el
}

function answerHeight(i) {
  const el = answerRefs.value[i]
  return el ? `${el.scrollHeight + 32}px` : '0px'
}

function toggle(i) {
  openIndex.value = openIndex.value === i ? -1 : i
}

const faqs = [
  {
    question: 'Combien coûte un site web ?',
    answer: 'Chaque projet est unique, donc chaque devis l\'est aussi. Le tarif dépend du type de site, du nombre de pages, des fonctionnalités souhaitées et du niveau de design attendu. Je fournis un devis détaillé, gratuit et sans engagement, après un premier échange pour comprendre votre besoin.',
  },
  {
    question: 'Quel est le délai de réalisation ?',
    answer: 'Ça dépend vraiment du projet. Un site vitrine peut être livré en moins de 2 semaines, parfois bien moins selon la complexité. Un projet plus ambitieux (e-commerce, outil métier) demande 4 à 8 semaines. Les délais dépendent aussi de votre réactivité sur les validations — plus on avance ensemble, plus on va vite.',
  },
  {
    question: 'Je n\'ai pas de contenu préparé, est-ce un problème ?',
    answer: 'Pas du tout. On peut commencer par définir la structure ensemble, et vous préparez le contenu en parallèle. Et si vous n\'en avez pas, je peux m\'en charger — c\'est un service que je propose (rédaction, sélection d\'images). Une légère marge s\'ajoute selon le volume, mais tout est discuté en amont.',
  },
  {
    question: 'WordPress ou sur-mesure — comment vous décidez ?',
    answer: 'Selon ce qui est le plus adapté à votre projet. Pour la majorité des sites vitrines et blogs, WordPress est la solution idéale : rapide à livrer, facile à gérer pour vous ensuite. Pour des besoins spécifiques ou des interfaces plus complexes, je développe sur-mesure — c\'est-à-dire à partir du code, sans système tout fait. Dans tous les cas, je choisis l\'outil qui sert votre projet — pas celui qui m\'arrange.',
  },
  {
    question: 'Le site sera-t-il optimisé pour Google (SEO) ?',
    answer: 'Oui, le SEO technique est intégré dès la conception : structure HTML sémantique, vitesse de chargement, balises meta, sitemap, compatibilité mobile. Pour aller plus loin (stratégie de contenu, netlinking), je peux vous accompagner ou vous orienter.',
  },
  {
    question: 'Que se passe-t-il après la livraison ?',
    answer: 'Je reste disponible pour toute question ou ajustement pendant 30 jours après la livraison. Ensuite, je propose des forfaits de maintenance pour les mises à jour, sauvegardes et évolutions. Vous n\'êtes jamais laissé sans support.',
  },
  {
    question: 'Puis-je modifier le site moi-même après livraison ?',
    answer: 'Oui, si c\'est votre souhait, je construis le site sur un CMS (WordPress, etc.) avec une formation à la prise en main. Vous pouvez modifier textes et images vous-même, facilement, depuis une interface simple — sans aucune connaissance technique.',
  },
  {
    question: 'Comment se passe le paiement ?',
    answer: 'En règle générale, un acompte est demandé au démarrage pour couvrir les outils et licences nécessaires au projet. La répartition exacte dépend ensuite de la nature et de la complexité du projet — plus il est robuste, plus les jalons sont structurés. Les modalités sont toujours discutées et formalisées avant le début du projet.',
  },
]
</script>

<style scoped>
.faq {
  background: #F8FAFC;
  padding: 120px 24px;
  position: relative;
}

.faq::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 800px;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.25), transparent);
}

.faq-container {
  max-width: 1100px;
  margin: 0 auto;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1), transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.faq-container.visible {
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
  line-height: 1.15;
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

.faq-container.visible .section-title::after {
  width: 60px;
}

.section-subtitle {
  font-size: 16px;
  color: #64748B;
}

.subtitle-link {
  color: #2563EB;
  font-weight: 600;
  border-bottom: 1px solid rgba(37, 99, 235, 0.3);
  transition: border-color 0.3s ease;
}

.subtitle-link:hover {
  border-color: #2563EB;
}

/* Layout */
.faq-grid {
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 48px;
  align-items: start;
}

/* FAQ list */
.faq-list {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.faq-item {
  border-bottom: 1px solid rgba(10, 15, 30, 0.08);
  overflow: hidden;
}

.faq-item:first-child {
  border-top: 1px solid rgba(10, 15, 30, 0.08);
}

.faq-question {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding: 22px 0;
  background: transparent;
  border: none;
  cursor: pointer;
  text-align: left;
  font-size: 16px;
  font-weight: 600;
  color: #0A0F1E;
  transition: color 0.3s ease;
}

@media (hover: hover) {
  .faq-question:hover { color: #2563EB; }
}

.faq-item.open .faq-question {
  color: #2563EB;
}

.faq-icon {
  flex-shrink: 0;
  width: 32px;
  height: 32px;
  background: rgba(37, 99, 235, 0.07);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #64748B;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.faq-item.open .faq-icon {
  background: rgba(37, 99, 235, 0.12);
  color: #2563EB;
  transform: rotate(180deg);
}

.faq-answer {
  overflow: hidden;
  transition: max-height 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.faq-answer-inner {
  padding-bottom: 20px;
}

.faq-answer-inner p {
  font-size: 15px;
  color: #64748B;
  line-height: 1.8;
}

/* Aside */
.faq-aside {
  display: flex;
  flex-direction: column;
  gap: 20px;
  position: sticky;
  top: 100px;
}

.faq-cta-card {
  background: #0A0F1E;
  border-radius: 20px;
  padding: 32px 28px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.cta-icon {
  font-size: 24px;
  color: #60A5FA;
  margin-bottom: 4px;
}

.faq-cta-card h3 {
  font-size: 18px;
  font-weight: 700;
  color: #F8FAFC;
  letter-spacing: -0.5px;
  line-height: 1.3;
}

.faq-cta-card p {
  font-size: 14px;
  color: rgba(248, 250, 252, 0.55);
  line-height: 1.6;
}

.faq-cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
  padding: 12px 20px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 14px;
  font-weight: 600;
  border-radius: 10px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

@media (hover: hover) {
  .faq-cta-btn:hover {
    background: #1d4ed8;
    box-shadow: 0 0 20px rgba(37, 99, 235, 0.5);
    transform: scale(1.02);
  }
}

.faq-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.stat {
  background: #FFFFFF;
  border: 1px solid rgba(10, 15, 30, 0.07);
  border-radius: 14px;
  padding: 20px 16px;
  display: flex;
  flex-direction: column;
  gap: 4px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.04);
  transition: all 0.3s ease;
}

@media (hover: hover) {
  .stat:hover {
    border-color: rgba(37, 99, 235, 0.2);
    box-shadow: 0 4px 16px rgba(37, 99, 235, 0.08);
  }
}

.stat strong {
  font-size: 22px;
  font-weight: 800;
  color: #2563EB;
  letter-spacing: -1px;
}

.stat span {
  font-size: 11.5px;
  color: #64748B;
  line-height: 1.4;
}

@media (max-width: 1024px) {
  .faq-grid {
    grid-template-columns: 1fr;
  }

  .faq-aside {
    position: static;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .faq-cta-card {
    flex: 1;
    min-width: 280px;
  }

  .faq-stats {
    flex: 1;
    min-width: 200px;
  }
}

@media (max-width: 768px) {
  .faq {
    padding: 80px 20px;
  }

  .faq-aside {
    flex-direction: column;
  }

  .section-header {
    margin-bottom: 48px;
  }

  .faq-question {
    font-size: 15px;
    padding: 18px 0;
  }
}
</style>
