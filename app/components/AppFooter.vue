<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const currentYear = new Date().getFullYear()

const items = ref<NavigationMenuItem[][]>([
  [
    {
      label: `System Engineering • © ${currentYear}`,
     
    }
  ]
])
</script>

<template>
  <div class="flex items-center gap-4">
    <UNavigationMenu color="neutral" variant="link" :items="items" class="w-full" />
    <UColorModeButton />
  </div>
</template>

