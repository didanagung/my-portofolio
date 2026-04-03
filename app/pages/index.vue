<template>
  <section class="h-full w-auto md:flex justify-center items-center">
    <div class="md:flex-1/2 flex items-center justify-center">
      <Hero />
    </div>
    <div class="md:flex-1/2 flex items-center">
      <div class="text-left md:text-right w-full">
        <h3 class="text-5xl font-light iam text-[#00a9be]" data-aos="flip-down">I'm a</h3>
        <h1 class="text-7xl font-extrabold" data-aos="flip-down" data-aos-delay="600">Fullstack</h1>
        <h1 class="text-7xl font-extrabold text-[#e33007]" data-aos="flip-down" data-aos-delay="1000">Web Developer</h1>
        <div class="flex flex-col md:flex-row gap-3 justify-end my-5">
          <span v-for="(skill, index) in skills" :key="index" class="text-center px-4 py-1 rounded-full border border-[#00a9be] hover:bg-[#e33007] hover:border-0" data-aos="fade-up" :data-aos-delay="(index + 1) * 200">
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = ref(["HTML", "JavaScript", "CSS", "PHP", "Go"])
</script>

<style scoped>
.iam {
  font-family: 'Mate', sans-serif;
}
</style>
