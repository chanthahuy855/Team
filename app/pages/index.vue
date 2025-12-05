<script setup lang="ts">
</script>

<template>
  <div>
    <!-- <UPageHero
      title="Nuxt Starter Template"
      description="A production-ready starter template powered by Nuxt UI. Build beautiful, accessible, and performant applications in minutes, not hours."
    /> -->
    
    <UPageSection >
      <UPageCTA
        title="System Engineering Team"
        description="Contact us if you want to automate your work..."
        variant="subtle"
        :links="[{
          label: 'Contact Us',
          to: '#',
          target: '_blank',
          trailingIcon: 'i-lucide-arrow-right',
          color: 'neutral'
        }, 
       
        ]"
      />
      <TeamGrid />
    </UPageSection>
    
  </div>
</template>
