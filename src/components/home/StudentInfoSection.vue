<template>
  <section ref="sectionRef" class="student-info-section w-full bg-brand-paper text-brand-black py-16 px-4 flex flex-col items-center relative overflow-hidden responsive-bubble-section">
    <div class="absolute inset-0 z-0 pointer-events-none select-none">
      <DecorativeLine
        :start="{ x: -80, y: 189.9 }"
        :segments="[
          { c1: { x: -61.33, y: 187.25 }, c2: { x: -41.83, y: 184.48 }, end: { x: 32, y: 174 } },
          { c1: { x: 105.83, y: 163.51 }, c2: { x: 333.83, y: 107.5 }, end: { x: 363, y: 127 } },
          { c1: { x: 392.16, y: 146.5 }, c2: { x: 221, y: 238.66 }, end: { x: 207, y: 291 } },
          { c1: { x: 193, y: 343.33 }, c2: { x: 277.83, y: 404.5 }, end: { x: 279, y: 441 } },
          { c1: { x: 280.16, y: 477.5 }, c2: { x: 212, y: 483.5 }, end: { x: 214, y: 510 } },
          { c1: { x: 216, y: 536.5 }, c2: { x: 300.66, y: 573.5 }, end: { x: 291, y: 600 } },
          { c1: { x: 281.33, y: 626.5 }, c2: { x: 174.66, y: 647.5 }, end: { x: 156, y: 669 } },
          { c1: { x: 137.33, y: 690.5 }, c2: { x: 192.33, y: 718.66 }, end: { x: 179, y: 729 } },
          { c1: { x: 165.66, y: 739.33 }, c2: { x: 119.16, y: 730.16 }, end: { x: 76, y: 731 } },
          { c1: { x: 32.83, y: 731.83 }, c2: { x: -54, y: 733.52 }, end: { x: -80, y: 734.02 } },
        ]"
        color="green"
        stroke-width="var(--decorative-line-stroke-width, 3.75em)"
        view-box="-120 100 600 700"
        :draw-duration="linesAnimated ? 1.2 : 0"
        :draw-delay="linesAnimated ? 0.2 : 0"
        class="absolute left-0 bottom-0 w-[min(100vw,700px)] h-auto max-h-[80vh] z-0 pointer-events-none -translate-x-80 -translate-y-16"
      />
      <DecorativeLine
        :start="{ x: 1636, y: -63.16 }"
        :segments="[
          { c1: { x: 1616.67, y: -46.63 }, c2: { x: 1560, y: 1.81 }, end: { x: 1520, y: 36 } },
          { c1: { x: 1480, y: 70.19 }, c2: { x: 1407, y: 105.83 }, end: { x: 1396, y: 142 } },
          { c1: { x: 1385, y: 178.17 }, c2: { x: 1449.33, y: 215.33 }, end: { x: 1454, y: 253 } },
          { c1: { x: 1458.67, y: 290.67 }, c2: { x: 1420.67, y: 326.83 }, end: { x: 1424, y: 368 } },
          { c1: { x: 1427.33, y: 409.17 }, c2: { x: 1491.33, y: 461.17 }, end: { x: 1474, y: 500 } },
          { c1: { x: 1456.67, y: 538.83 }, c2: { x: 1316.83, y: 576.17 }, end: { x: 1320, y: 601 } },
          { c1: { x: 1323.17, y: 625.83 }, c2: { x: 1465.5, y: 632.33 }, end: { x: 1493, y: 649 } },
          { c1: { x: 1520.5, y: 665.67 }, c2: { x: 1461.17, y: 692.33 }, end: { x: 1485, y: 701 } },
          { c1: { x: 1508.83, y: 709.67 }, c2: { x: 1610.83, y: 701 }, end: { x: 1636, y: 701 } },
        ]"
        color="purple"
        stroke-width="var(--decorative-line-stroke-width, 3.75em)"
        view-box="1300 -100 400 850"
        :draw-duration="linesAnimated ? 1.2 : 0"
        :draw-delay="linesAnimated ? 0.5 : 0"
        class="absolute right-0 top-0 w-[min(100vw,700px)] h-auto max-h-[80vh] z-0 pointer-events-none translate-x-72 translate-y-4"
      />
    </div>
    <div class="relative z-10 w-full flex flex-col items-center">
      <div class="max-w-3xl text-center mb-10">
        <h2 class="text-lg md:text-2xl font-normal mb-4 leading-relaxed">
          <span class="font-bold">ELOQEE</span> je platforma pro rozvoj měkkých kompetencí, bez kterých se dneska neobjdeš. Pro studenty organizujeme <span class="font-bold">ELOQEE Challenge</span>, která tě skrz praktické výzvy připraví na realitu.
        </h2>
      </div>
      <div class="w-full flex flex-col items-center mb-10">
        <div class="bubble-row-wrapper">
          <div class="bubble-row justify-center">
            <span class="bubble bg-brand-green ml-24">Udělej dobrý první dojem</span>
            <span class="bubble bg-brand-magenta ml-8">Prosaď svoje názory mezi ostatními</span>
            <span class="bubble bg-brand-purple ml-20">Zazáři na pohovoru v nejlepším světle</span>
          </div>
          <div class="bubble-row justify-center mt-2">
            <span class="bubble bg-brand-purple ml-4">Získej podporu na svoje nápady</span>
            <span class="bubble bg-brand-green ml-32">Nahlížej kriticky na složité problémy</span>
            <span class="bubble bg-brand-magenta">Nesesipej se v náročných situacích</span>
          </div>
        </div>
      </div>
      <div class="max-w-3xl text-center mb-8">
        <p class="text-base md:text-lg text-brand-black/70">
          Spojujeme akademickou půdu se skutečnými nároky trhu práce a moderního světa.<br>
          <span class="font-bold">Chceš být u toho?</span>
        </p>
      </div>
      <form v-if="!submitted" @submit.prevent="handleSubmit" class="w-full max-w-md mx-auto flex flex-col items-center gap-4">
        <input
          v-model="email"
          type="email"
          :placeholder="submitted ? 'Díky, dáme ti vědět.' : 'Tvůj e-mail'"
          class="w-full rounded-full border border-brand-purple/30 px-6 py-3 text-base focus:outline-none focus:ring-2 focus:ring-brand-purple"
          :disabled="loading"
          required
        />
        <div class="flex items-center w-full">
          <input
            v-model="consent"
            type="checkbox"
            id="gdpr"
            class="rounded mr-2 accent-brand-purple focus:ring-brand-purple focus:ring-2"
            :disabled="loading"
            required
          />
          <label for="gdpr" class="text-xs text-brand-black/70">Souhlasím, že si můžete uložit můj mail a poslat mi info před další ELOQEE Challenge</label>
        </div>
        <button
          type="submit"
          class="w-full rounded-full bg-brand-purple text-brand-white font-semibold py-3 px-6 mt-2 text-base shadow-md hover:bg-brand-purple/90 transition"
          :disabled="loading"
        >
          {{ loading ? 'Odesílám...' : 'Dejte mi vědět před dalším ročníkem' }}
        </button>
        <div v-if="errorMsg" class="text-sm text-red-600 mt-2">{{ errorMsg }}</div>
      </form>
      <div v-else class="w-full max-w-md mx-auto flex flex-col items-center gap-4 py-8">
        <div class="text-lg font-semibold text-brand-green mb-2">Děkujeme!</div>
        <div class="text-base text-brand-black/80">Tvůj e-mail byl úspěšně uložen. Ozveme se před dalším ročníkem.</div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'
import DecorativeLine from '../DecorativeLine.vue'

const email = ref('')
const consent = ref(false)
const loading = ref(false)
const submitted = ref(false)
const linesVisible = ref(false)
const linesAnimated = ref(false)
const sectionRef = ref<HTMLElement | null>(null)
const errorMsg = ref('')

async function handleSubmit() {
  if (!email.value || !consent.value) return
  loading.value = true
  errorMsg.value = ''
  try {
    const res = await fetch('https://script.google.com/macros/s/AKfycbyCb0kFyx7QLBum80zfVrCpocj8_e-YtXQuMAba9u9drslQli6e1Q6TRx2qCABbwqY/exec', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ email: email.value, souhlas: 'Ano' })
    })
    if (!res.ok) {
      errorMsg.value = 'Odeslání se nezdařilo. Zkuste to prosím později.'
      console.error('Chyba při odesílání:', await res.text())
      return
    }
    email.value = ''
    submitted.value = true
  } catch (e) {
    errorMsg.value = 'Odeslání se nezdařilo. Zkuste to prosím později.'
    console.error('Chyba při fetch:', e)
  } finally {
    loading.value = false
  }
}

let observer: IntersectionObserver | null = null
onMounted(() => {
  observer = new window.IntersectionObserver(
    ([entry]) => {
      linesVisible.value = entry.isIntersecting
      if (entry.isIntersecting) linesAnimated.value = true
    },
    { threshold: 0.15 }
  )
  if (sectionRef.value) observer.observe(sectionRef.value)
})
onBeforeUnmount(() => {
  if (observer && sectionRef.value) observer.unobserve(sectionRef.value)
})
</script>

<style scoped>
.responsive-bubble-section {
  --decorative-line-stroke-width: 3.75em;
}
@media (max-width: 48rem) {
  .responsive-bubble-section {
    --decorative-line-stroke-width: 2em;
  }
}

.bubble {
  display: inline-block;
  font-weight: 600;
  font-size: 1rem;
  padding: 1.1em 3.2em;
  border-radius: 999px;
  margin: 0.3em 0.15em;
  box-shadow: 0 2px 16px rgba(0,0,0,0.06);
  text-align: center;
  color: #fff;
  transition: transform 0.15s;
  white-space: nowrap;
  max-width: 100vw;
  overflow: hidden;
  text-overflow: ellipsis;
  min-width: 14rem;
}
.bg-brand-purple {
  background: var(--color-brand-purple);
}
.bg-brand-green {
  background: var(--color-brand-green);
}
.bg-brand-magenta {
  background: var(--color-brand-magenta);
}
.bubble:hover { transform: scale(1.04); }

.flex.flex-wrap {
  row-gap: 0.3em;
  column-gap: 0.3em;
}

@media (min-width: 768px) {
  .flex.flex-wrap {
    flex-wrap: wrap;
    max-width: 700px;
  }
  .bubble {
    font-size: 1.05rem;
    padding: 1.1em 2.1em;
  }
}

@media (min-width: 640px) {
  .flex.flex-wrap {
    flex-wrap: wrap;
    max-width: 700px;
  }
}

@media (max-width: 639px) {
  .flex.flex-wrap {
    flex-wrap: wrap;
    max-width: 420px;
  }
}

.bubble-row-wrapper {
  width: 100%;
  max-width: 1100px;
}

.bubble-row {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
  gap: 0.5em;
  margin-bottom: 0.2em;
  min-height: 3.2em;
}

@media (max-width: 639px) {
  .bubble-row-wrapper {
    max-width: 420px;
  }
  .bubble-row {
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.3em;
    min-height: unset;
  }
  .bubble-row + .bubble-row {
    margin-top: 0.5em;
  }
  .bubble {
    margin-left: 0 !important;
    min-width: unset;
    padding-left: 1.2em;
    padding-right: 1.2em;
  }
}

.bezier-overlay {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 10;
}
.bezier-overlay :deep(canvas),
.bezier-overlay :deep(svg),
.bezier-overlay :deep(.absolute) {
  pointer-events: auto;
}
</style>
