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
              <span class="badge-icon" aria-hidden="true">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5" />
                </svg>
              </span>
              <div>
                <strong>Réponse sous 24h</strong>
                <span>Toujours</span>
              </div>
            </li>
            <li class="contact-badge">
              <span class="badge-icon" aria-hidden="true">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
                  <path fill-rule="evenodd" d="M12 1.5a5.25 5.25 0 0 0-5.25 5.25v3a3 3 0 0 0-3 3v6.75a3 3 0 0 0 3 3h10.5a3 3 0 0 0 3-3v-6.75a3 3 0 0 0-3-3v-3c0-2.9-2.35-5.25-5.25-5.25Zm3.75 8.25v-3a3.75 3.75 0 1 0-7.5 0v3h7.5Z" clip-rule="evenodd" />
                </svg>
              </span>
              <div>
                <strong>Confidentialité garantie</strong>
                <span>Vos informations restent privées</span>
              </div>
            </li>
            <li class="contact-badge">
              <span class="badge-icon" aria-hidden="true">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
                  <path fill-rule="evenodd" d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25Zm-1.902 7.098a3.75 3.75 0 0 1 3.903-.884.75.75 0 1 0 .498-1.415A5.25 5.25 0 0 0 8.005 9.75H7.5a.75.75 0 0 0 0 1.5h.054a5.281 5.281 0 0 0 0 1.5H7.5a.75.75 0 0 0 0 1.5h.505a5.25 5.25 0 0 0 6.494 2.701.75.75 0 1 0-.498-1.415 3.75 3.75 0 0 1-4.252-1.286h3.001a.75.75 0 0 0 0-1.5H9.075a3.77 3.77 0 0 1 0-1.5h3.675a.75.75 0 0 0 0-1.5h-3c.105-.14.221-.274.348-.402Z" clip-rule="evenodd" />
                </svg>
              </span>
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
                <div class="input-wrap" :class="{ 'input-error': errors.name }">
                  <svg class="input-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0ZM4.501 20.118a7.5 7.5 0 0 1 14.998 0A17.933 17.933 0 0 1 12 21.75c-2.676 0-5.216-.584-7.499-1.632Z" />
                  </svg>
                  <input
                    id="name"
                    v-model="form.name"
                    type="text"
                    class="form-field"
                    placeholder="Votre nom"
                    required
                    autocomplete="name"
                    aria-required="true"
                    :aria-invalid="!!errors.name"
                  />
                </div>
                <span v-if="errors.name" class="form-error" role="alert">{{ errors.name }}</span>
              </div>

              <div class="form-group">
                <label for="email" class="form-label">Email</label>
                <div class="input-wrap" :class="{ 'input-error': errors.email }">
                  <svg class="input-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 0 1-2.25 2.25h-15a2.25 2.25 0 0 1-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25m19.5 0v.243a2.25 2.25 0 0 1-1.07 1.916l-7.5 4.615a2.25 2.25 0 0 1-2.36 0L3.32 8.91a2.25 2.25 0 0 1-1.07-1.916V6.75" />
                  </svg>
                  <input
                    id="email"
                    v-model="form.email"
                    type="email"
                    class="form-field"
                    placeholder="votre@email.com"
                    required
                    autocomplete="email"
                    aria-required="true"
                    :aria-invalid="!!errors.email"
                  />
                </div>
                <span v-if="errors.email" class="form-error" role="alert">{{ errors.email }}</span>
              </div>
            </div>

            <div class="form-group">
              <label for="phone" class="form-label">
                Téléphone
                <span class="form-optional">(optionnel)</span>
              </label>
              <div class="input-wrap">
                <svg class="input-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 0 0 2.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 0 1-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 0 0-1.091-.852H4.5A2.25 2.25 0 0 0 2.25 4.5v2.25Z" />
                </svg>
                <input
                  id="phone"
                  v-model="form.phone"
                  type="tel"
                  class="form-field"
                  placeholder="+33 6 00 00 00 00"
                  autocomplete="tel"
                />
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
              <span v-if="!submitting">
                Envoyer ma demande
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3" />
                </svg>
              </span>
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
  phone: '',
  projectType: '',
  message: '',
})

const errors = reactive({})
const submitted = ref(false)
const submitting = ref(false)

// ── Demo state ──
const demoForm = reactive({ name: '', email: '', message: '' })
const demoFocus = reactive({ name: false, email: false, message: false })

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
  try {
    const res = await fetch('https://formspree.io/f/xwvrqazk', {
      method: 'POST',
      headers: { 'Accept': 'application/json', 'Content-Type': 'application/json' },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        phone: form.phone || '—',
        projectType: form.projectType,
        message: form.message,
      }),
    })
    if (!res.ok) throw new Error()
    submitted.value = true
  } catch {
    errors.message = 'Une erreur est survenue. Réessayez ou contactez-moi sur WhatsApp.'
  } finally {
    submitting.value = false
  }
}

function resetForm() {
  form.name = ''
  form.email = ''
  form.phone = ''
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
  color: #2563EB;
  flex-shrink: 0;
}

.badge-icon svg {
  width: 18px;
  height: 18px;
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

@media (hover: hover) {
  .contact-direct-whatsapp:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 32px rgba(22, 163, 74, 0.4);
    background: linear-gradient(135deg, #15803d 0%, #166534 100%);
  }
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

@media (hover: hover) {
  .contact-direct-whatsapp:hover .whatsapp-arrow {
    transform: translateX(4px);
    color: #ffffff;
  }
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
  letter-spacing: 0.2px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.input-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
  height: 50px;
  padding: 0 14px;
  background: #FFFFFF;
  border: 1.5px solid rgba(10, 15, 30, 0.12);
  border-radius: 12px;
  transition: border-color 0.22s ease, box-shadow 0.22s ease;
}

.input-wrap:focus-within {
  border-color: #2563EB;
  box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
}

.input-wrap.input-error {
  border-color: #EF4444;
  box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.1);
}

.input-icon {
  width: 17px;
  height: 17px;
  color: #94A3B8;
  flex-shrink: 0;
  transition: color 0.22s ease;
}

.input-wrap:focus-within .input-icon {
  color: #2563EB;
}

.form-field {
  flex: 1;
  border: none;
  outline: none;
  background: transparent;
  font-size: 15px;
  color: #0A0F1E;
  font-family: inherit;
  height: 100%;
}

.form-field::placeholder {
  color: #94A3B8;
}

.form-input {
  padding: 13px 16px;
  background: #FFFFFF;
  border: 1.5px solid rgba(10, 15, 30, 0.12);
  border-radius: 12px;
  font-size: 15px;
  color: #0A0F1E;
  transition: border-color 0.22s ease, box-shadow 0.22s ease;
  outline: none;
  width: 100%;
  font-family: inherit;
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
  height: 50px;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%2364748B' stroke-width='2'%3E%3Cpath d='m6 9 6 6 6-6'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 14px center;
  padding-right: 44px;
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.form-optional {
  font-size: 12px;
  font-weight: 400;
  color: #94A3B8;
}

.form-error {
  font-size: 12px;
  color: #EF4444;
  font-weight: 500;
}

/* ── Submit gradient + shimmer ── */
.form-submit {
  width: 100%;
  padding: 15px 24px;
  background: linear-gradient(135deg, #2563EB 0%, #7C3AED 100%);
  color: #F8FAFC;
  font-size: 15px;
  font-weight: 600;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  font-family: inherit;
  margin-top: 4px;
  position: relative;
  overflow: hidden;
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1),
              box-shadow 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.form-submit > span {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  position: relative;
  z-index: 1;
}

.form-submit svg {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
  transition: transform 0.3s ease;
}

.form-submit::after {
  content: '';
  position: absolute;
  top: -60%;
  left: -80%;
  width: 50%;
  height: 220%;
  background: linear-gradient(105deg, transparent, rgba(255, 255, 255, 0.28), transparent);
  transform: skewX(-20deg);
  pointer-events: none;
}

@media (hover: hover) {
  .form-submit:hover:not(:disabled) {
    transform: scale(1.01);
    box-shadow: 0 0 32px rgba(37, 99, 235, 0.5), 0 0 16px rgba(124, 58, 237, 0.3);
  }
  .form-submit:hover:not(:disabled)::after {
    animation: form-shimmer 0.55s ease forwards;
  }
  .form-submit:hover:not(:disabled) svg {
    transform: translateX(4px);
  }
}

@keyframes form-shimmer {
  to { left: 130%; }
}

.form-submit:disabled {
  opacity: 0.65;
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

@media (hover: hover) {
  .success-reset:hover {
    background: #2563EB;
    color: white;
  }
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

/* ════════════════════════════════
   DEMO — aperçu design amélioré
   ════════════════════════════════ */
.demo-section {
  max-width: 600px;
  margin: 80px auto 0;
  padding: 0 24px 80px;
}

.demo-eyebrow {
  text-align: center;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #94A3B8;
  margin-bottom: 20px;
}

/* Card blanche avec ombre nette */
.demo-card {
  background: #FFFFFF;
  border-radius: 20px;
  padding: 36px;
  box-shadow:
    0 1px 2px rgba(0, 0, 0, 0.04),
    0 4px 12px rgba(0, 0, 0, 0.06),
    0 16px 48px rgba(0, 0, 0, 0.08);
}

.demo-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.demo-field-group {
  width: 100%;
}

/* ── Floating label wrapper ── */
.demo-wrap {
  position: relative;
  height: 56px;
  background: #F8FAFC;
  border: 1.5px solid rgba(10, 15, 30, 0.1);
  border-radius: 12px;
  transition: border-color 0.22s ease, box-shadow 0.22s ease, background 0.22s ease;
  overflow: hidden;
}

.demo-wrap--textarea {
  height: auto;
  margin-top: 16px;
}

/* Gradient border au focus */
.demo-wrap:focus-within {
  border-color: transparent;
  background-image:
    linear-gradient(#F8FAFC, #F8FAFC),
    linear-gradient(135deg, #2563EB, #8B5CF6);
  background-origin: border-box;
  background-clip: padding-box, border-box;
  box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
}

/* Floating label */
.demo-label {
  position: absolute;
  left: 14px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 15px;
  font-weight: 400;
  color: #94A3B8;
  pointer-events: none;
  transition: top 0.2s ease, transform 0.2s ease, font-size 0.2s ease,
              font-weight 0.2s ease, color 0.2s ease;
  white-space: nowrap;
}

.demo-wrap--textarea .demo-label {
  top: 18px;
  transform: none;
}

.demo-wrap.demo-active .demo-label,
.demo-wrap:focus-within .demo-label {
  top: 10px;
  transform: none;
  font-size: 11px;
  font-weight: 600;
  color: #2563EB;
  letter-spacing: 0.3px;
}

.demo-wrap--textarea.demo-active .demo-label,
.demo-wrap--textarea:focus-within .demo-label {
  top: 10px;
}

/* Input field sans bordure */
.demo-input {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 32px;
  padding: 0 14px;
  background: transparent;
  border: none;
  outline: none;
  font-size: 15px;
  color: #0A0F1E;
  font-family: inherit;
}

.demo-textarea {
  position: relative;
  height: auto;
  padding: 28px 14px 12px;
  resize: none;
  width: 100%;
  min-height: 110px;
}

/* Séparateur */
.demo-sep {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(10, 15, 30, 0.07), transparent);
  margin: 20px 0 0;
}

/* ── Submit avec gradient + shimmer ── */
.demo-submit {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  margin-top: 24px;
  padding: 15px 24px;
  background: linear-gradient(135deg, #2563EB 0%, #7C3AED 100%);
  color: #F8FAFC;
  font-size: 15px;
  font-weight: 600;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  font-family: inherit;
  position: relative;
  overflow: hidden;
  transition: opacity 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
}

.demo-submit svg {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
  transition: transform 0.3s ease;
}

.demo-submit::after {
  content: '';
  position: absolute;
  top: -60%;
  left: -80%;
  width: 50%;
  height: 220%;
  background: linear-gradient(105deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transform: skewX(-20deg);
  pointer-events: none;
}

@media (hover: hover) {
  .demo-submit:hover {
    transform: scale(1.01);
    box-shadow: 0 0 32px rgba(37, 99, 235, 0.5), 0 0 16px rgba(124, 58, 237, 0.3);
  }
  .demo-submit:hover::after {
    animation: demo-shimmer 0.55s ease forwards;
  }
  .demo-submit:hover svg {
    transform: translateX(4px);
  }
}

@keyframes demo-shimmer {
  to { left: 130%; }
}

@media (max-width: 600px) {
  .demo-row {
    grid-template-columns: 1fr;
  }
  .demo-card {
    padding: 24px 20px;
  }
}
</style>
