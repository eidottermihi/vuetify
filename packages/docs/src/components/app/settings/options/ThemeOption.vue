<template>
  <v-radio-group
    v-model="user.theme"
    color="#70a2d8"
    hide-details
    true-icon="mdi-check-circle-outline"
  >
    <v-radio
      v-for="(item, i) in items"
      :key="i"
      :disabled="item.disabled"
      :value="item.value"
    >
      <template #label>
        <v-icon :icon="item.icon" start />

        {{ item.text }}
      </template>
    </v-radio>
  </v-radio-group>

  <v-defaults-provider
    :defaults="{
      VIcon: {
        color: user.mixedTheme ? 'primary' : 'disabled'
      }
    }"
  >
    <v-switch
      v-model="user.mixedTheme"
      class="ps-3 flex-0-0"
      color="primary"
      inset
      label="Dark Code Blocks"
      messages="Change all code blocks to use a dark theme."
      true-icon="mdi-check"
      false-icon="$close"
    />
  </v-defaults-provider>
</template>

<script setup lang="ts">
  // Composables
  import { useUserStore } from '@/store/user'
  import { useI18n } from 'vue-i18n'

  const user = useUserStore()
  const { t } = useI18n()

  const items = [
    {
      text: t('light'),
      icon: 'mdi-white-balance-sunny',
      value: 'light',
    },
    {
      text: t('dark'),
      icon: 'mdi-weather-night',
      value: 'dark',
    },
    {
      text: t('system'),
      icon: 'mdi-desktop-tower-monitor',
      value: 'system',
    },
    {
      text: t('blackguard'),
      icon: 'mdi-space-invaders',
      disabled: true,
      value: 'blackguard',
    },
  ]
</script>
