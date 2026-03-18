<script setup lang="ts">
import HomePage from './pages/HomePage.vue'
import PalettePage from './pages/PalettePage.vue'

const normalizedPath = window.location.pathname.replace(/\/+$/, '') || '/'
const isPaletteRoute = normalizedPath === '/palette'
</script>

<template>
  <PalettePage v-if="isPaletteRoute" />
  <HomePage v-else />
</template>