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
  <main class="min-h-[100dvh] overflow-x-hidden bg-brand-paper text-brand-black">
    <section
      class="relative h-[100dvh] w-full overflow-hidden transition-colors duration-300"
      :class="isCompanyMode ? 'bg-brand-paper' : 'bg-brand-surface'"
    >
      <div
        class="pointer-events-none absolute inset-y-0 left-1/2 h-full -translate-x-1/2"
        style="width: calc(100dvh * 16 / 9)"
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
        class="absolute inset-0 z-[1] h-full w-full translate-x-24 opacity-100"
      />

      <DecorativeLine
        :start="{ x: -20.803108808290162, y: -167.5 }"
        :segments="[
          {
            c1: { x: -9.936096718480143, y: -143.66666666666666 },
            c2: { x: 0.9309153713298735, y: -119.83333333333333 },
            end: { x: 11.797927461139892, y: -96 },
          },
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
        class="absolute inset-0 z-[2] h-full w-full -translate-x-24 translate-y-8 opacity-100"
      />

      <DecorativeLine
        :start="{ x: -96, y: 29.57894736842104 }"
        :segments="[
          {
            c1: { x: -79.33333333333333, y: 57.649122807017534 },
            c2: { x: -38, y: 127.26315789473684 },
            end: { x: 4, y: 198 },
          },
          {
            c1: { x: 46, y: 268.7368421052632 },
            c2: { x: 100.66666666666666, y: 381.1666666666667 },
            end: { x: 156, y: 454 },
          },
          {
            c1: { x: 211.33333333333334, y: 526.8333333333334 },
            c2: { x: 357, y: 625 },
            end: { x: 336, y: 635 },
          },
          {
            c1: { x: 315, y: 645 },
            c2: { x: 29.833333333333332, y: 487.1666666666667 },
            end: { x: 30, y: 514 },
          },
          {
            c1: { x: 30.166666666666668, y: 540.8333333333334 },
            c2: { x: 341, y: 757.1666666666666 },
            end: { x: 337, y: 796 },
          },
          {
            c1: { x: 333, y: 834.8333333333334 },
            c2: { x: 78.16666666666667, y: 757.6832829808661 },
            end: { x: 6, y: 747 },
          },
          {
            c1: { x: -66.16666666666667, y: 736.3167170191339 },
            c2: { x: -79, y: 734.416918429003 },
            end: { x: -96, y: 731.9003021148036 },
          },
        ]"
        view-box="-96 -96 1632 1017"
        color="green"
        class="absolute inset-0 z-0 h-full w-full -translate-x-32 translate-y-8 opacity-100"
      />

      <DecorativeLine
        :start="{ x: -318, y: 768.1818181818182 }"
        :segments="[
          {
            c1: { x: -299.5, y: 760.8939393939394 },
            c2: { x: -262.5, y: 746.3181818181819 },
            end: { x: -244, y: 739.030303030303 },
          },
          {
            c1: { x: -225.5, y: 731.7424242424242 },
            c2: { x: -188.5, y: 717.1666666666667 },
            end: { x: -170, y: 709.8787878787879 },
          },
          {
            c1: { x: -151.5, y: 702.5909090909091 },
            c2: { x: -114.5, y: 688.0151515151515 },
            end: { x: -96, y: 680.7272727272727 },
          },
          {
            c1: { x: -77.5, y: 673.439393939394 },
            c2: { x: -47.5, y: 661.6212121212121 },
            end: { x: 15, y: 637 },
          },
          {
            c1: { x: 77.5, y: 612.3787878787879 },
            c2: { x: 224.33333333333334, y: 527.3333333333334 },
            end: { x: 279, y: 533 },
          },
          {
            c1: { x: 333.6666666666667, y: 538.6666666666666 },
            c2: { x: 307, y: 660.6666666666666 },
            end: { x: 343, y: 671 },
          },
          {
            c1: { x: 379, y: 681.3333333333334 },
            c2: { x: 445, y: 579.8333333333334 },
            end: { x: 495, y: 595 },
          },
          {
            c1: { x: 545, y: 610.1666666666666 },
            c2: { x: 594.8483033932135, y: 707.6666666666666 },
            end: { x: 643, y: 762 },
          },
          {
            c1: { x: 691.1516966067865, y: 816.3333333333334 },
            c2: { x: 760.4251497005988, y: 894.5 },
            end: { x: 783.9101796407185, y: 921 },
          },
        ]"
        view-box="-96 -96 1632 1017"
        color="magenta"
        class="absolute inset-0 z-[1] h-full w-full translate-x-32 translate-y-36 opacity-100"
      />
      </div>

      <div class="relative z-10 mx-auto flex h-full max-w-6xl items-center justify-center px-6 md:px-10">
        <div class="flex w-full max-w-5xl -translate-y-5 flex-col gap-6 md:-translate-y-8 lg:-translate-y-10">
          <img
            :src="currentLogo"
            alt="Eloqee"
            class="w-full max-w-[800px] self-start transition-opacity duration-300 md:translate-x-6 md:translate-y-5 lg:max-w-[860px] lg:translate-x-12 lg:translate-y-8"
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