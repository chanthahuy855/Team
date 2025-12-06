<script setup>
  useHead({
    meta: [
      { name: 'viewport', content: 'width=device-width, initial-scale=1' }
    ],
    link: [
      { rel: 'icon', href: '/favicon.ico' }
    ],
    htmlAttrs: {
      lang: 'en'
    }
  })

  const title = 'System Engineering Team'
  const description = 'System Engineering Team focused on delivering solutions for Robotic Process Automation (RPA), E-Form workflows, Front-End applications, and Data Visualization'

  useSeoMeta({
    title,
    description,
    ogTitle: title,
    ogDescription: description,
    ogImage:'images/se-team.png',
    twitterImage:'images/se-team.png',
    twitterCard:'summary_large_image'
  })
</script>

<template>
  <UApp>
    <!-- <UHeader >
      <template #left>
        <NuxtLink to="/">
           System Engineering
        </NuxtLink>
 
      </template>
      <template #right>
            <UColorModeButton />
      </template>
    </UHeader> -->

    <UMain>
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>
    </UMain>

    <USeparator icon="" />
    <AppFooter />

    <!-- <UFooter :ui="{root:'fixed  bottom-0 left-0 right-0 h-14 bg-slate-50 dark:bg-gray-800 border-t border-gray-200 dark:border-gray-700 flex justify-around content-center  items-center shadow-lg z-10'}" >
      <template #left>
        <p class="text-sm text-muted">
          System Engineering • © {{ new Date().getFullYear() }}
        </p>
        <p>
          <UColorModeButton />
        </p>
          

      </template>

    </UFooter> -->
  </UApp>
</template>
