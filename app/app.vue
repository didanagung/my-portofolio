<script setup>
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/ujang.jpg' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Didan Agung Sergia Portofolio'
const description = 'Seorang Fullstack web developer yang selalu ingin terus belajar. Tertarik dengan bahasa go atau golang dan laravel.'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: '/homepage.png',
  twitterImage: '/homepage.png',
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
