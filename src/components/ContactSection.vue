<template>
  <section class="contact" aria-labelledby="contact-title">
    <div ref="sectionEl" class="contact-container" :class="{ visible: isVisible }">
      <div class="section-header">
        <span class="section-label" aria-hidden="true">— Contact</span>
        <h2 id="contact-title" class="section-title">Un projet en tête ?</h2>
        <p class="section-subtitle">Décrivez-le moi, je vous réponds sous 24h.</p>
      </div>

      <div class="contact-layout">
        <!-- Info side -->
        <aside class="contact-info" aria-label="Informations de contact">
          <p class="contact-pitch">
            Je réponds personnellement à chaque message. Pas de réponse automatique,
            pas de template — une vraie conversation pour comprendre votre besoin.
          </p>

          <ul class="contact-badges" role="list">
            <li class="contact-badge">
              <span class="badge-icon" aria-hidden="true">✉</span>
              <div>
                <strong>Réponse sous 24h</strong>
                <span>Toujours</span>
              </div>
            </li>
            <li class="contact-badge">
              <span class="badge-icon" aria-hidden="true">⊘</span>
              <div>
                <strong>Confidentialité garantie</strong>
                <span>Vos informations restent privées</span>
              </div>
            </li>
            <li class="contact-badge">
              <span class="badge-icon" aria-hidden="true">◇</span>
              <div>
                <strong>Devis gratuit et sans engagement</strong>
                <span>Estimation précise et transparente</span>
              </div>
            </li>
          </ul>

          <div class="contact-direct" aria-label="Contact direct">
            <p class="contact-direct-label">Contact direct</p>
            <a
              href="https://wa.me/33769661315"
              class="contact-direct-whatsapp"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="Écrire sur WhatsApp"
            >
              <span class="direct-icon" aria-hidden="true">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                  <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
                </svg>
              </span>
              <span class="whatsapp-text">
                <strong>Écrire sur WhatsApp</strong>
                <small>Réponse rapide garantie</small>
              </span>
              <span class="whatsapp-arrow" aria-hidden="true">→</span>
            </a>
          </div>
        </aside>

        <!-- Form side -->
        <div class="contact-form-wrap">
          <form
            v-if="!submitted"
            class="contact-form"
            @submit.prevent="handleSubmit"
            novalidate
            aria-label="Formulaire de contact"
          >
            <div class="form-row">
              <div class="form-group">
                <label for="name" class="form-label">Nom complet</label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  class="form-input"
                  :class="{ error: errors.name }"
                  placeholder="Jean Dupont"
                  required
                  autocomplete="name"
                  aria-required="true"
                  :aria-invalid="!!errors.name"
                />
                <span v-if="errors.name" class="form-error" role="alert">{{ errors.name }}</span>
              </div>

              <div class="form-group">
                <label for="email" class="form-label">Email</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  class="form-input"
                  :class="{ error: errors.email }"
                  placeholder="jean@exemple.com"
                  required
                  autocomplete="email"
                  aria-required="true"
                  :aria-invalid="!!errors.email"
                />
                <span v-if="errors.email" class="form-error" role="alert">{{ errors.email }}</span>
              </div>
            </div>

            <div class="form-group">
              <label for="project-type" class="form-label">Type de projet</label>
              <select
                id="project-type"
                v-model="form.projectType"
                class="form-input form-select"
                :class="{ error: errors.projectType }"
                required
                aria-required="true"
                :aria-invalid="!!errors.projectType"
              >
                <option value="" disabled>Sélectionnez un type</option>
                <option value="vitrine">Site vitrine</option>
                <option value="ecommerce">E-commerce</option>
                <option value="refonte">Refonte</option>
                <option value="crm">CRM ou outil métier</option>
                <option value="forum">Forum / Communauté</option>
                <option value="autre">Autre</option>
              </select>
              <span v-if="errors.projectType" class="form-error" role="alert">{{ errors.projectType }}</span>
            </div>

            <div class="form-group">
              <label for="message" class="form-label">Décrivez votre projet</label>
              <textarea
                id="message"
                v-model="form.message"
                class="form-input form-textarea"
                :class="{ error: errors.message }"
                placeholder="Décrivez votre projet, vos objectifs, votre délai estimé..."
                rows="5"
                required
                aria-required="true"
                :aria-invalid="!!errors.message"
              ></textarea>
              <span v-if="errors.message" class="form-error" role="alert">{{ errors.message }}</span>
            </div>

            <button type="submit" class="form-submit" :disabled="submitting">
              <span v-if="!submitting">Envoyer ma demande</span>
              <span v-else class="submitting">Envoi en cours...</span>
            </button>
          </form>

          <!-- Success state -->
          <div v-else class="form-success" role="status" aria-live="polite">
            <div class="success-icon" aria-hidden="true">✓</div>
            <h3>Message envoyé !</h3>
            <p>Merci pour votre message. Je vous réponds dans les 24h.</p>
            <button class="success-reset" @click="resetForm">Envoyer un nouveau message</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { useIntersection } from '../composables/useIntersection.js'

const { el: sectionEl, isVisible } = useIntersection({ threshold: 0.1 })

const form = reactive({
  name: '',
  email: '',
  projectType: '',
  message: '',
})

const errors = reactive({})
const submitted = ref(false)
const submitting = ref(false)

function validate() {
  Object.keys(errors).forEach(k => delete errors[k])
  let valid = true

  if (!form.name.trim()) {
    errors.name = 'Veuillez entrer votre nom.'
    valid = false
  }
  if (!form.email.trim()) {
    errors.email = 'Veuillez entrer votre email.'
    valid = false
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
    errors.email = 'Adresse email invalide.'
    valid = false
  }
  if (!form.projectType) {
    errors.projectType = 'Veuillez sélectionner un type de projet.'
    valid = false
  }
  if (!form.message.trim()) {
    errors.message = 'Veuillez décrire votre projet.'
    valid = false
  } else if (form.message.trim().length < 20) {
    errors.message = 'Merci d\'écrire au moins 20 caractères.'
    valid = false
  }

  return valid
}

async function handleSubmit() {
  if (!validate()) return
  submitting.value = true
  await new Promise(resolve => setTimeout(resolve, 900))
  submitting.value = false
  submitted.value = true
}

function resetForm() {
  form.name = ''
  form.email = ''
  form.projectType = ''
  form.message = ''
  submitted.value = false
}
</script>

<style scoped>
.contact {
  background: #FFFFFF;
  padding: 120px 24px;
  position: relative;
}

.contact::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 800px;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.2), transparent);
}

.contact-container {
  max-width: 1100px;
  margin: 0 auto;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1), transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.contact-container.visible {
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
  margin-bottom: 12px;
}

.section-subtitle {
  font-size: 17px;
  color: #64748B;
  font-style: italic;
}

.contact-layout {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 60px;
  align-items: start;
}

.contact-pitch {
  font-size: 16px;
  color: #64748B;
  line-height: 1.8;
  margin-bottom: 40px;
}

.contact-badges {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.contact-badge {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.badge-icon {
  width: 40px;
  height: 40px;
  background: rgba(37, 99, 235, 0.08);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  color: #2563EB;
  flex-shrink: 0;
}

.contact-badge strong {
  display: block;
  font-size: 14px;
  font-weight: 600;
  color: #0A0F1E;
  margin-bottom: 2px;
}

.contact-badge span {
  font-size: 13px;
  color: #64748B;
}

/* Contact direct */
.contact-direct {
  margin-top: 32px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.contact-direct-label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #94A3B8;
  margin-bottom: 2px;
}

.contact-direct-whatsapp {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 16px 20px;
  border-radius: 14px;
  background: linear-gradient(135deg, #16a34a 0%, #15803d 100%);
  color: #ffffff;
  font-size: 15px;
  font-weight: 600;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 4px 20px rgba(22, 163, 74, 0.25);
}

.contact-direct-whatsapp:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 32px rgba(22, 163, 74, 0.4);
  background: linear-gradient(135deg, #15803d 0%, #166534 100%);
}

.direct-icon {
  display: flex;
  align-items: center;
  flex-shrink: 0;
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 10px;
  justify-content: center;
}

.whatsapp-text {
  display: flex;
  flex-direction: column;
  gap: 2px;
  flex: 1;
}

.whatsapp-text strong {
  font-size: 15px;
  font-weight: 700;
  color: #ffffff;
}

.whatsapp-text small {
  font-size: 12px;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.7);
}

.whatsapp-arrow {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.7);
  transition: transform 0.3s ease;
}

.contact-direct-whatsapp:hover .whatsapp-arrow {
  transform: translateX(4px);
  color: #ffffff;
}

/* Form */
.contact-form-wrap {
  position: relative;
}

.contact-form {
  background: rgba(37, 99, 235, 0.03);
  border: 1px solid rgba(37, 99, 235, 0.12);
  border-radius: 24px;
  padding: 40px;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow: 0 4px 30px rgba(37, 99, 235, 0.05);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 20px;
}

.form-label {
  font-size: 13px;
  font-weight: 600;
  color: #0A0F1E;
  letter-spacing: 0.3px;
}

.form-input {
  padding: 13px 16px;
  background: #FFFFFF;
  border: 1.5px solid rgba(10, 15, 30, 0.12);
  border-radius: 12px;
  font-size: 15px;
  color: #0A0F1E;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  outline: none;
  width: 100%;
}

.form-input::placeholder {
  color: #94A3B8;
}

.form-input:focus {
  border-color: #2563EB;
  box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
}

.form-input.error {
  border-color: #EF4444;
  box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.1);
}

.form-select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%2364748B' stroke-width='2'%3E%3Cpath d='m6 9 6 6 6-6'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 14px center;
  padding-right: 44px;
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.form-error {
  font-size: 12px;
  color: #EF4444;
  font-weight: 500;
}

.form-submit {
  width: 100%;
  padding: 15px 24px;
  background: #2563EB;
  color: #F8FAFC;
  font-size: 15px;
  font-weight: 600;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  margin-top: 4px;
}

.form-submit:hover:not(:disabled) {
  background: #1d4ed8;
  box-shadow: 0 0 28px rgba(37, 99, 235, 0.5), 0 4px 12px rgba(37, 99, 235, 0.3);
  transform: scale(1.01);
}

.form-submit:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.submitting {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.submitting::after {
  content: '';
  width: 14px;
  height: 14px;
  border: 2px solid rgba(255, 255, 255, 0.4);
  border-top-color: white;
  border-radius: 50%;
  animation: spin 0.7s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

/* Success state */
.form-success {
  background: rgba(37, 99, 235, 0.04);
  border: 1px solid rgba(37, 99, 235, 0.15);
  border-radius: 24px;
  padding: 60px 40px;
  text-align: center;
}

.success-icon {
  width: 64px;
  height: 64px;
  background: linear-gradient(135deg, #2563EB, #60A5FA);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  color: white;
  margin: 0 auto 24px;
}

.form-success h3 {
  font-size: 24px;
  font-weight: 700;
  color: #0A0F1E;
  margin-bottom: 12px;
}

.form-success p {
  font-size: 16px;
  color: #64748B;
  margin-bottom: 32px;
}

.success-reset {
  padding: 12px 28px;
  background: transparent;
  border: 1.5px solid #2563EB;
  color: #2563EB;
  font-size: 14px;
  font-weight: 600;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.success-reset:hover {
  background: #2563EB;
  color: white;
}

@media (max-width: 1024px) {
  .contact-layout {
    grid-template-columns: 1fr;
    gap: 48px;
  }
}

@media (max-width: 768px) {
  .contact {
    padding: 80px 20px;
  }

  .contact-form {
    padding: 28px 20px;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .section-header {
    margin-bottom: 48px;
  }
}
</style>
