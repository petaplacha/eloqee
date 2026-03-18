<script setup lang="ts">
import { computed, ref } from 'vue'
import DecorativeLine from '../components/DecorativeLine.vue'
import studentLogo from '../assets/logo-bila.svg'
import companyLogo from '../assets/logo.svg'

type HeroMode = 'student' | 'company'

const heroMode = ref<HeroMode>('student')

const isCompanyMode = computed(() => heroMode.value === 'company')
const currentLogo = computed(() => (isCompanyMode.value ? companyLogo : studentLogo))

const toggleButtonClass = (mode: HeroMode) => {
  const isActive = heroMode.value === mode

  if (isActive) {
    return isCompanyMode.value
      ? 'bg-brand-black text-brand-white shadow-sm'
      : 'bg-brand-white text-brand-black shadow-sm'
  }

  return isCompanyMode.value
    ? 'text-brand-black/60 hover:text-brand-black'
    : 'text-brand-white/72 hover:text-brand-white'
}
</script>

<template>
  <main class="min-h-screen overflow-x-hidden bg-brand-paper text-brand-black">
    <section
      class="relative h-[100svh] max-h-[100svh] w-full max-w-[100vw] overflow-hidden transition-colors duration-300"
      :class="isCompanyMode ? 'bg-brand-paper' : 'bg-brand-surface'"
    >
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
        class="absolute inset-0 z-0 h-full w-full translate-x-20 opacity-100"
      />

      <DecorativeLine
        :start="{ x: 11.797927461139892, y: -96 }"
        :segments="[
          {
            c1: { x: 22.66493955094991, y: -72.16666666666667 },
            c2: { x: 51.46632124352331, y: -9 },
            end: { x: 77, y: 47 },
          },
          {
            c1: { x: 102.53367875647669, y: 103 },
            c2: { x: 193.83333333333334, y: 207.83333333333334 },
            end: { x: 165, y: 240 },
          },
          {
            c1: { x: 136.16666666666666, y: 272.1666666666667 },
            c2: { x: -52.5, y: 240 },
            end: { x: -96, y: 240 },
          },
        ]"
        view-box="-96 -96 1632 1017"
        color="purple"
        class="absolute inset-0 z-0 h-full w-full -translate-x-20 opacity-100"
      />

      <div class="relative z-10 mx-auto flex h-full max-w-6xl items-center justify-center px-6 md:px-10">
        <div class="flex w-full max-w-5xl -translate-y-5 flex-col gap-6 md:-translate-y-8 lg:-translate-y-10">
          <img
            :src="currentLogo"
            alt="Eloqee"
            class="w-full max-w-[780px] self-start transition-opacity duration-300 md:translate-x-6 md:translate-y-5 lg:max-w-[840px] lg:translate-x-12 lg:translate-y-8"
          >

          <div class="w-full max-w-[640px] self-end text-left md:-translate-y-4 md:translate-x-1 lg:translate-x-2">
            <h1
              class="text-3xl font-bold leading-tight transition-colors duration-300 md:text-5xl"
              :class="isCompanyMode ? 'text-brand-black' : 'text-brand-white'"
            >
              Klíč, jak mít budoucnost trochu víc pod kontrolou!
            </h1>
            <p
              class="mt-4 text-base leading-relaxed transition-colors duration-300 md:text-xl"
              :class="isCompanyMode ? 'text-brand-black/70' : 'text-brand-white/72'"
            >
              Budujeme generaci studentů s ambicí a měkkými kompetencemi, která mění svět. Staň se součástí a připrav se na budoucnost.
            </p>
          </div>
        </div>
      </div>

      <div class="absolute bottom-[8em] left-1/2 z-20 -translate-x-1/2">
        <div
          class="inline-flex rounded-full p-1 transition-colors duration-300"
          :class="isCompanyMode
            ? 'border border-brand-black/10 bg-brand-white shadow-[0_12px_40px_rgba(0,0,0,0.08)]'
            : 'border border-brand-white/12 bg-brand-white/10 shadow-[0_12px_40px_rgba(0,0,0,0.2)] backdrop-blur-md'"
        >
          <button
            type="button"
            class="rounded-full px-5 py-2 text-sm font-semibold transition-colors duration-300"
            :class="toggleButtonClass('student')"
            @click="heroMode = 'student'"
          >
            Pro studenty
          </button>
          <button
            type="button"
            class="rounded-full px-5 py-2 text-sm font-semibold transition-colors duration-300"
            :class="toggleButtonClass('company')"
            @click="heroMode = 'company'"
          >
            Pro partnery
          </button>
        </div>
      </div>
    </section>
  </main>
</template>