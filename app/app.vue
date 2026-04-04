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

const judul = 'Didan Agung Sergia Portofolio'
const title = "Didan Agung Sergia - Fullstack Web Developer"
const description = 'Seorang Fullstack web developer yang selalu ingin terus belajar. Tertarik dengan bahasa go atau golang dan laravel.'
const ngaranDewek = 'Didan Agung Sergia'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: '/homepage.png',
  twitterImage: '/homepage.png',
  twitterCard: 'summary_large_image',
  author: ngaranDewek,
  ogType: "website",
  ogSiteName: judul
})

const loading = ref(true)
onMounted(() => {
  const alreadyLoaded = sessionStorage.getItem('loaded')

  if (!alreadyLoaded) {
    setTimeout(() => {
      loading.value = false
      sessionStorage.setItem('loaded', 'true')
    }, 2000)
  } else {
    loading.value = false
  }
})
</script>

<template>
  <FullScreenLoader :show="loading" />
  <div class="px-5 py-3 h-screen flex flex-col">
    <Navbar />

    <main class="flex-1 w-full overflow-y-auto">
      <NuxtPage />
    </main>

    <Footer />
  </div>
</template>
