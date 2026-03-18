<script setup lang="ts">
const colors = [
  { name: 'brand-surface', hex: '#303030', text: 'text-brand-white', swatch: 'bg-brand-surface border border-brand-white/10' },
  { name: 'brand-black', hex: '#000000', text: 'text-brand-white', swatch: 'bg-brand-black border border-brand-white/10' },
  { name: 'brand-purple', hex: '#4200F6', text: 'text-brand-white', swatch: 'bg-brand-purple' },
  { name: 'brand-green', hex: '#00DF82', text: 'text-brand-black', swatch: 'bg-brand-green' },
  { name: 'brand-coral', hex: '#FF4733', text: 'text-brand-black', swatch: 'bg-brand-coral' },
  { name: 'brand-lime', hex: '#CFF665', text: 'text-brand-black', swatch: 'bg-brand-lime' },
  { name: 'brand-aqua', hex: '#9CF0E3', text: 'text-brand-black', swatch: 'bg-brand-aqua' },
  { name: 'brand-magenta', hex: '#F238A7', text: 'text-brand-white', swatch: 'bg-brand-magenta' },
  { name: 'brand-pink', hex: '#FFB3CF', text: 'text-brand-black', swatch: 'bg-brand-pink' },
  { name: 'brand-white', hex: '#FFFFFF', text: 'text-brand-black', swatch: 'bg-brand-white' },
]
</script>

<template>
  <main class="min-h-screen bg-brand-surface px-6 py-12 text-brand-white md:px-10">
    <section class="mx-auto flex max-w-6xl flex-col gap-8">
      <div class="space-y-3">
        <p class="text-sm font-bold uppercase tracking-[0.18em] text-brand-green">/palette</p>
        <h1 class="text-4xl font-bold md:text-5xl">Barevná paleta</h1>
        <p class="max-w-3xl text-brand-white/72">
          Primární akcenty jsou `#4200F6` a `#00DF82` na tmavém povrchu `#303030`.
        </p>
      </div>

      <div class="grid gap-4 sm:grid-cols-2 xl:grid-cols-3">
        <article
          v-for="color in colors"
          :key="color.name"
          class="rounded-[28px] p-5 shadow-[0_0_0_1px_rgba(255,255,255,0.06)]"
          :class="[color.swatch, color.text]"
        >
          <p class="text-sm font-semibold uppercase tracking-[0.14em]">{{ color.name }}</p>
          <p class="mt-10 text-2xl font-bold">{{ color.hex }}</p>
        </article>
      </div>
    </section>
  </main>
</template>