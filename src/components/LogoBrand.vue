<template>
  <!-- ═══════════════════════════════════════════════
       VARIANTE A — Carré monogramme + STUDIO
       ─ IB dans un rectangle bleu arrondi, STUDIO léger à droite
  ══════════════════════════════════════════════════ -->
  <svg v-if="variant === 'A'"
    :height="height"
    viewBox="0 0 148 36"
    xmlns="http://www.w3.org/2000/svg"
    :aria-label="label"
    role="img"
    class="logo-brand"
    fill="none"
  >
    <rect x="0" y="0" width="40" height="36" rx="8" fill="#2563EB"/>
    <text x="20" y="25" text-anchor="middle"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="800" font-size="18" fill="#FFFFFF" letter-spacing="-0.5"
    >IB</text>
    <text x="50" y="23"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="300" font-size="12" fill="#F8FAFC" letter-spacing="3"
    >STUDIO</text>
  </svg>

  <!-- ═══════════════════════════════════════════════
       VARIANTE B — Stacked : IB grand / ligne / STUDIO
       ─ Format vertical compact, ligne bleue entre les deux
  ══════════════════════════════════════════════════ -->
  <svg v-else-if="variant === 'B'"
    :height="height"
    viewBox="0 0 72 40"
    xmlns="http://www.w3.org/2000/svg"
    :aria-label="label"
    role="img"
    class="logo-brand"
    fill="none"
  >
    <text x="2" y="22"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="800" font-size="22" fill="#2563EB" letter-spacing="-1"
    >IB</text>
    <rect x="2" y="26" width="68" height="1.5" rx="1" fill="#2563EB" opacity="0.5"/>
    <text x="2" y="38"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="300" font-size="10" fill="#F8FAFC" letter-spacing="4"
    >STUDIO</text>
  </svg>

  <!-- ═══════════════════════════════════════════════
       VARIANTE C — Slash diagonal IB / STUDIO
       ─ IB blanc · slash bleu incliné · STUDIO light
  ══════════════════════════════════════════════════ -->
  <svg v-else-if="variant === 'C'"
    :height="height"
    viewBox="0 0 152 36"
    xmlns="http://www.w3.org/2000/svg"
    :aria-label="label"
    role="img"
    class="logo-brand"
    fill="none"
  >
    <text x="0" y="27"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="800" font-size="28" fill="#F8FAFC" letter-spacing="-1"
    >IB</text>
    <!-- Slash incliné -->
    <line x1="48" y1="32" x2="57" y2="4" stroke="#2563EB" stroke-width="2" stroke-linecap="round"/>
    <text x="63" y="25"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="300" font-size="12.5" fill="#F8FAFC" letter-spacing="2.5"
    >STUDIO</text>
  </svg>

  <!-- ═══════════════════════════════════════════════
       VARIANTE D — IB en dégradé + point + STUDIO
       ─ IB avec gradient bleu vif → bleu clair, point bleu, STUDIO blanc
  ══════════════════════════════════════════════════ -->
  <svg v-else
    :height="height"
    viewBox="0 0 158 36"
    xmlns="http://www.w3.org/2000/svg"
    :aria-label="label"
    role="img"
    class="logo-brand"
    fill="none"
  >
    <defs>
      <linearGradient id="ibGrad" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="#2563EB"/>
        <stop offset="100%" stop-color="#60A5FA"/>
      </linearGradient>
    </defs>
    <text x="2" y="27"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="800" font-size="28" fill="url(#ibGrad)" letter-spacing="-1"
    >IB</text>
    <circle cx="50" cy="18" r="3.5" fill="#2563EB"/>
    <text x="60" y="25"
      font-family="Inter, -apple-system, sans-serif"
      font-weight="300" font-size="12.5" fill="#F8FAFC" letter-spacing="2.5"
    >STUDIO</text>
  </svg>
</template>

<script setup>
defineProps({
  variant: {
    type: String,
    default: 'D', // ← change ici pour tester : 'A', 'B', 'C' ou 'D'
  },
  height: {
    type: Number,
    default: 30,
  },
  label: {
    type: String,
    default: 'IB Studio',
  },
})
</script>

<style scoped>
.logo-brand {
  display: block;
  flex-shrink: 0;
  width: auto;
}
</style>
