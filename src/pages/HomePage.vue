<script setup lang="ts">
import DecorativeLine from '../components/DecorativeLine.vue'
import logo from '../assets/logo-bila.svg'
</script>

<template>
  <main class="relative min-h-screen overflow-hidden bg-brand-surface px-6 py-12 text-brand-white md:px-10">
    <DecorativeLine
      :start="{ x: 974.3695652173913, y: -500 }"
      :segments="[
        {
          c1: { x: 1000, y: -140 },
          c2: { x: 1121.2282608695652, y: -19.666666666666664 },
          end: { x: 1186, y: 14 },
        },
        {
          c1: { x: 1250.7717391304348, y: 47.666666666666664 },
          c2: { x: 1337.8333333333333, y: 52.666666666666664 },
          end: { x: 1363, y: 106 },
        },
        {
          c1: { x: 1388.1666666666667, y: 159.33333333333334 },
          c2: { x: 1330.1666666666667, y: 261.3333333333333 },
          end: { x: 1337, y: 334 },
        },
        {
          c1: { x: 1343.8333333333333, y: 406.6666666666667 },
          c2: { x: 1418.6666666666667, y: 482.6666666666667 },
          end: { x: 1404, y: 542 },
        },
        {
          c1: { x: 1389.3333333333333, y: 601.3333333333334 },
          c2: { x: 1247.5, y: 659.8333333333334 },
          end: { x: 1249, y: 690 },
        },
        {
          c1: { x: 1250.5, y: 720.1666666666666 },
          c2: { x: 1365.1666666666667, y: 713.375 },
          end: { x: 1413, y: 723 },
        },
        {
          c1: { x: 1460.8333333333333, y: 732.625 },
          c2: { x: 1515.5, y: 743.625 },
          end: { x: 1800, y: 747.75 },
        },
      ]"
      view-box="-96 -224 1632 1145"
      color="magenta"
      class="absolute inset-0 z-0 h-full w-full opacity-90"
    />

    <section class="relative z-10 mx-auto flex min-h-screen max-w-6xl items-center justify-center">
      <div class="flex w-full max-w-5xl -translate-y-5 flex-col gap-6 md:-translate-y-8 lg:-translate-y-10">
        <img
          :src="logo"
          alt="Eloqee"
          class="w-full max-w-[720px] self-start md:translate-y-5 md:-translate-x-1 lg:translate-y-8 lg:-translate-x-2"
        >

        <div class="w-full max-w-[640px] self-end text-left md:-translate-y-4 md:translate-x-1 lg:translate-x-2">
          <h1 class="text-3xl font-bold leading-tight text-brand-white md:text-5xl">
            Klíč, jak mít budoucnost trochu víc pod kontrolou!
          </h1>
          <p class="mt-4 text-base leading-relaxed text-brand-white/72 md:text-xl">
            Budujeme generaci studentů s ambicí a měkkými kompetencemi, která mění svět. Staň se součástí a připrav se na budoucnost.
          </p>
        </div>
      </div>
    </section>
  </main>
</template>