<script setup lang="ts">
import { computed } from 'vue'
import { useTheme } from 'vuetify'

const theme = useTheme()

const isDark = computed({
  get: () => theme.global.name.value === 'dark',
  set: (value: boolean) => {
    theme.global.name.value = value ? 'dark' : 'light'
  },
})

const links = [
  { label: 'Portfolio', url: 'https://www.paigelane.com', icon: 'mdi-briefcase-outline' },
  { label: 'Dribbble', url: 'https://dribbble.com', icon: 'mdi-dribbble' },
  { label: 'LinkedIn', url: 'https://www.linkedin.com', icon: 'mdi-linkedin' },
  { label: 'Email', url: 'mailto:paige@paigelane.com', icon: 'mdi-email-outline' },
]
</script>

<template>
  <main class="page-shell">
    <div class="profile-card">
      <div class="header-row">
        <div class="spacer" />
        <v-btn
          :icon="isDark ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent'"
          variant="text"
          class="theme-toggle"
          aria-label="Toggle theme"
          @click="isDark = !isDark"
        />
      </div>

      <div class="profile-wrap">
        <v-avatar size="112" class="profile-avatar">
          <span class="profile-initials">PL</span>
        </v-avatar>
      </div>

      <div class="title-block">
        <h1>Paige Lane</h1>
        <p>Designer + frontend developer building thoughtful digital experiences.</p>
      </div>

      <nav class="link-stack" aria-label="Social links">
        <v-btn
          v-for="link in links"
          :key="link.label"
          class="link-button"
          :href="link.url"
          target="_blank"
          rel="noreferrer"
          variant="flat"
          color="surface"
          block
          rounded="xl"
          size="large"
        >
          <template #prepend>
            <v-icon :icon="link.icon" />
          </template>
          {{ link.label }}
        </v-btn>
      </nav>
    </div>
  </main>
</template>

<style scoped>
.page-shell {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 24px 16px;
}

.profile-card {
  width: min(100%, 480px);
  background: rgba(18, 24, 38, 0.82);
  border: 1px solid rgba(148, 163, 184, 0.2);
  border-radius: 28px;
  box-shadow: 0 24px 80px rgba(15, 23, 42, 0.35);
  backdrop-filter: blur(14px);
  padding: 20px 20px 24px;
}

.header-row {
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

.spacer {
  flex: 1;
}

.theme-toggle {
  width: 42px;
  height: 42px;
  border-radius: 50%;
}

.profile-wrap {
  display: flex;
  justify-content: center;
  margin-top: 8px;
}

.profile-avatar {
  background: linear-gradient(135deg, #8b5cf6 0%, #38bdf8 100%);
  border: 3px solid rgba(255, 255, 255, 0.18);
  box-shadow: 0 12px 24px rgba(96, 165, 250, 0.3);
}

.profile-initials {
  font-size: 1.65rem;
  font-weight: 700;
  letter-spacing: 0.08em;
}

.title-block {
  text-align: center;
  margin-top: 18px;
}

.title-block h1 {
  margin: 0;
  font-size: clamp(2.1rem, 5vw, 2.8rem);
  line-height: 1.1;
  letter-spacing: -0.06em;
}

.title-block p {
  margin: 10px auto 0;
  max-width: 30ch;
  color: rgba(226, 232, 240, 0.8);
  font-size: 1rem;
  line-height: 1.6;
}

.link-stack {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-top: 22px;
}

.link-button {
  justify-content: flex-start;
  font-weight: 600;
  letter-spacing: 0.01em;
  transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
}

.link-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 22px rgba(59, 130, 246, 0.2);
}

@media (max-width: 420px) {
  .profile-card {
    padding: 18px 16px 20px;
  }

  .title-block p {
    font-size: 0.95rem;
  }
}
</style>
