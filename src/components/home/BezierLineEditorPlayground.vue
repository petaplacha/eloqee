<template>
  <section class="bezier-editor-section w-full min-h-[60vh] bg-brand-paper flex flex-col items-center justify-center py-12">
    <h2 class="text-xl font-bold mb-6">Návrh Bezierových čar</h2>
    <BezierLineEditor color="magenta" />
  </section>
</template>

<script setup lang="ts">
import BezierLineEditor from '../BezierLineEditor.vue'
</script>

<style scoped>
.bezier-editor-section {
  border: 2px dashed var(--color-brand-magenta);
  border-radius: 2rem;
  margin: 2rem 0;
}
</style>
