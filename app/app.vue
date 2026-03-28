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

const title = 'Didan Portofolio'
const description = 'Seorang Fullstack web developer yang selalu ingin belajar.'

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
  <div class="px-5 py-3 h-screen flex flex-col overflow-hidden">
    <Navbar />

    <main class="flex-1 w-full overflow-y-auto">
      <NuxtPage />
    </main>

    <Footer />
  </div>
</template>
