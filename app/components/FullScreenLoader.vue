<template>
  <div
    v-if="show"
    class="fixed inset-0 z-[9999] flex flex-col gap-5 items-center justify-center bg-[#0f172b] transition-opacity duration-700"
    :class="show ? 'opacity-100' : 'opacity-0'"
  >
    <div class="text-5xl text-center font-extrabold flex flex-col gap-3 iam">
      <h1>Hi 👋</h1>
    </div>
    <div class="animate-spin rounded-full h-16 w-16 border-t-4 border-white"></div>
  </div>
</template>

<script setup>
defineProps({
  show: Boolean
})
</script>

<style scoped>
.iam {
  font-family: 'Tinos', sans-serif;
}
</style>
