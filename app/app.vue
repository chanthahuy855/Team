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
  const description = 'A contact Portfolio for System Engineering Team to Support Robots'

  useSeoMeta({
    title,
    description,
    ogTitle: title,
    ogDescription: description,
    ogImage: 'https://ui.nuxt.com/assets/templates/nuxt/starter-light.png',
    twitterImage: 'https://ui.nuxt.com/assets/templates/nuxt/starter-light.png',
    twitterCard: 'summary_large_image'
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
