<template>
  <section class="most-important-section">
    <TextWithUnderlines
      text="Focusing on What Truly Matters"
      class="sub-heading"
      v-bind="mainHeading"
    />
    <TextWithBolds
      text="Elevate your brand to the top of the food chain with web solutions from Webociraptor."
      class="sub-title"
      v-bind="firstText"
    />
    <GoldButton :clickFunction="show" />
    <ContactForm ref="dialogTarget" />
    <BenefitsList :start="5" />
  </section>
</template>

<script setup>
const mainHeading = {
  underlined: ['Truly Matters'],
}

const firstText = {
  boldText: ['the top of the food chain'],
  sizeClass: 'size-26px',
}

const dialogTarget = ref(null)
const show = () => dialogTarget.value?.show()
</script>

<style scoped>
.most-important-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 447px;
  grid-template-areas: 'left right';
  margin-top: 5.4375rem;
  margin-bottom: 12.8125rem;
}

.gold-button {
  grid-area: left;
  align-self: flex-end;
  font-size: 1.25rem;
  width: 100%;
  max-width: 23.75rem;
  height: 4.5rem;
}

.sub-heading {
  grid-area: left;
  height: 10.875rem;
}

.sub-title {
  grid-area: left;
  max-width: 25.6875rem;
  height: 9.25rem;
  margin-top: 11.5rem;
}

.benefits {
  align-self: flex-end;
  height: auto;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 769px) and (max-width: 1000px) {
  .most-important-section {
    grid-template-columns: 51.8% auto;
    grid-template-rows: auto;
    grid-template-areas: 'left right';
    margin-top: 5.4375rem;
    margin-bottom: 12.8125rem;
    min-height: 27.9375rem;
    gap: 0 5vw;
  }

  .benefits {
    min-height: 21rem;
  }
}

@media screen and (max-width: 768px) {
  .most-important-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 4rem;
    margin-bottom: 8rem;
  }

  .sub-heading {
    order: 1;
    height: auto;
    align-self: self-start;
  }

  .benefits {
    order: 2;
    margin-top: clamp(3rem, 6vw, 4rem);
    width: 100%;
    min-height: 26rem;
  }

  .sub-title {
    order: 3;
    margin-top: clamp(3rem, 6vw, 4rem);
  }

  .gold-button {
    order: 4;
    margin-top: clamp(3rem, 6vw, 4rem);
    align-self: center;
  }
}

@media screen and (max-width: 375px) {
  .most-important-section {
    margin-top: 8rem;
    margin-bottom: 6rem;
  }
}
</style>
