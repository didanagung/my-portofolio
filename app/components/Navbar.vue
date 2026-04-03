<template>
  <div class="flex p-4 w-full">
    <div class="flex-1/2 md:flex-1/3">
      <h1 class="ngaran font-bold text-2xl">
        <NuxtLink to="/">
          DAS
        </NuxtLink>
      </h1>
    </div>
    <div class="flex-2/3 justify-items-end hidden md:block">
      <div class="flex flex-row gap-3">
        <div v-for="(item, index) in menu" :key="index" class="mt-1">
          <NuxtLink :to="item.direct" class="hover:border-b" :class="route.path == item.direct ? 'text-[#e33007]' : ''"> {{ item.title }} </NuxtLink>
        </div>
        <div>
          <UColorModeButton />
        </div>
      </div>
    </div>
    <div class="flex-1/2 flex justify-end items-center md:hidden">
      <UIcon :name="menuToast ? 'i-heroicons-x-mark' : 'i-heroicons-bars-3'" class="w-8 h-8" @click="showHideMenu"/>
    </div>
  </div>

  <div
    class="fixed bottom-0 left-0 w-full z-50 p-4 shadow bg-amber-50 dark:bg-[#0f172b] text-center transition-all duration-1000"
    :class="menuToast ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-full pointer-events-none'"
  >
    <div v-for="(item, index) in menu" :key="index" class="mt-5">
      <NuxtLink :to="item.direct" class="hover:border-b" :class="route.path == item.direct ? 'text-[#e33007]' : ''" @click="menuToast = false"> {{ item.title }} </NuxtLink>
    </div>
    <div>
      <UColorModeButton />
    </div>
  </div>
</template>

<script setup>
  const route = useRoute()
  const menuToast = ref(false)
  const menu = ref([
    {
      title: "Home",
      direct: "/"
    },
    {
      title: "About",
      direct: "/about"
    },
    {
      title: "Skills",
      direct: "/skills"
    },
    // {
    //   title: "Projects",
    //   direct: "/projects"
    // },
    {
      title: "Contact",
      direct: "/contact"
    },
  ])

  const showHideMenu = () => {menuToast.value = !menuToast.value}

</script>

<style scoped>
.ngaran {
  font-family: 'Lora', sans-serif;
}
</style>
