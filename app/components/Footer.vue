<template>
  <div class="text-center mt-auto">
    <h1> © {{ year }}</h1>
  </div>
</template>

<script setup>
const year = new Date().getFullYear()
</script>
