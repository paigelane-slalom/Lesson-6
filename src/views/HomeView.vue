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
  <v-container fluid class="d-flex align-center justify-center min-vh-100 pa-4">
    <v-card
      class="mx-auto pa-4 page-card"
      width="100%"
      max-width="480"
      rounded="xl"
      elevation="12"
    >
      <v-row no-gutters justify="end">
        <v-col cols="auto">
          <v-btn
            :icon="isDark ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent'"
            variant="text"
            aria-label="Toggle theme"
            class="theme-toggle"
            @click="isDark = !isDark"
          />
        </v-col>
      </v-row>

      <v-row justify="center" class="mt-2">
        <v-col cols="auto">
          <v-avatar size="112" class="profile-avatar">
            <span class="profile-initials">PL</span>
          </v-avatar>
        </v-col>
      </v-row>

      <v-row justify="center" class="mt-4">
        <v-col cols="12">
          <h1 class="text-center text-h3 font-weight-bold mb-2">Paige Lane</h1>
          <p class="text-center text-body-1 text-medium-emphasis mb-0">
            Designer + frontend developer building thoughtful digital experiences.
          </p>
        </v-col>
      </v-row>

      <v-row class="mt-6" dense>
        <v-col cols="12">
          <v-btn
            v-for="link in links"
            :key="link.label"
            :href="link.url"
            :target="link.url.startsWith('http') ? '_blank' : undefined"
            :rel="link.url.startsWith('http') ? 'noreferrer' : undefined"
            block
            class="mb-3 link-button"
            color="surface"
            rounded="xl"
            size="large"
            variant="flat"
          >
            <template #prepend>
              <v-icon :icon="link.icon" />
            </template>
            {{ link.label }}
          </v-btn>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<style scoped>
.min-vh-100 {
  min-height: 100vh;
}

.page-card {
  background: rgba(18, 24, 38, 0.82);
  border: 1px solid rgba(148, 163, 184, 0.2);
  box-shadow: 0 24px 80px rgba(15, 23, 42, 0.35);
  backdrop-filter: blur(14px);
}

.theme-toggle {
  width: 42px;
  height: 42px;
  border-radius: 50%;
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

.link-button {
  justify-content: flex-start;
  font-weight: 600;
  letter-spacing: 0.01em;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.link-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 22px rgba(59, 130, 246, 0.2);
}
</style>
