<template>
  <section class="student-info-section w-full bg-brand-paper text-brand-black py-16 px-4 flex flex-col items-center">
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
          <span class="bubble bg-brand-magenta">Nesesypej se v náročných situacích</span>
        </div>
      </div>
    </div>
    <div class="max-w-3xl text-center mb-8">
      <p class="text-base md:text-lg text-brand-black/70">
        Spojujeme akademickou půdu se skutečnými nároky trhu práce a moderního světa.<br>
        <span class="font-bold">Chceš být u toho?</span>
      </p>
    </div>
    <form class="w-full max-w-md mx-auto flex flex-col items-center gap-4">
      <input type="email" placeholder="Tvůj e-mail" class="w-full rounded-full border border-brand-purple/30 px-6 py-3 text-base focus:outline-none focus:ring-2 focus:ring-brand-purple" />
      <div class="flex items-center w-full">
        <input type="checkbox" id="gdpr" class="rounded mr-2" />
        <label for="gdpr" class="text-xs text-brand-black/70">Souhlasím, že si můžete uložit můj mail a poslat mi info před další ELOQEE Challenge</label>
      </div>
      <button type="button" class="w-full rounded-full bg-brand-purple text-brand-white font-semibold py-3 px-6 mt-2 text-base shadow-md hover:bg-brand-purple/90 transition">Dejte mi vědět před dalším ročníkem</button>
    </form>
  </section>
</template>

<style scoped>
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
</style>
