<template>
  <section class="h-full flex flex-col md:flex-row justify-center items-center">
    <div class="flex-1/2 flex items-center justify-start md:justify-center">
      <h1 class="font-extrabold text-3xl md:text-6xl text-[#00a9be]">
        Skills
      </h1>
    </div>
    <div class="flex-1/2 flex items-center justify-center">
      <div class="w-full grid grid-cols-3 lg:grid-cols-4 gap-4">
        <UPageCard
          v-for="(data, i) in dataImage"
          :key="i"
          class="flex justify-center items-center h-16 md:h-32"
          spotlight
        >
          <div class="flex justify-center items-center w-full h-12 md:h-20">
            <img
              :src="`/skills/${data}.png`"
              :alt="data"
              class="w-full h-full object-contain"
            />
          </div>
        </UPageCard>
      </div>
    </div>
  </section>
</template>

<script setup>
  const dataImage = ref(['html','css','js','php','go','laravel','node','nuxt','vue','tailwind','pgsql','mongo'])
</script>

<style scoped>
  .desc {
    font-family: 'Inter', sans-serif;
  }
</style>
