<template>
  <section class="first-section">
    <div class="left-section">
      <TextWithUnderlines
        text="Dominant web solutions for every brand"
        class="sub-heading"
        v-bind="mainHeading"
      />
      <TextWithBolds
        text="With our dynamic Webociraptor team, we'll turn your ideas into powerful and aesthetically perfect websites that leave the competition far behind."
        class="sub-title"
        v-bind="firstText"
      />
    </div>
    <LogoBadges />
    <BenefitsList :start="0" :end="5" />
    <TextWithBolds
      text="Elevate your brand to the top of the food chain with web solutions from Webociraptor."
      class="sub-text"
      v-bind="secondText"
    />
    <GoldButton :clickFunction="show" />
    <ContactForm ref="dialogTarget" />
  </section>
</template>

<script setup>
const mainHeading = {
  underlined: ['solutions'],
}
const firstText = {
  boldText: ['powerful and aesthetically perfect'],
  sizeClass: 'size-24px',
}

const secondText = {
  boldText: ['the top of the food chain'],
  sizeClass: 'size-22px',
}

const dialogTarget = ref(null)
const show = () => dialogTarget.value?.show()
</script>

<style scoped>
.first-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 101px 405px 118px;
  grid-template-areas:
    'left-section logos'
    'left-section list'
    'sub-text audit-btn';
  margin-top: 4.8125rem;
  gap: 0 10%;
}

.left-section {
  grid-area: left-section;
}

.sub-heading {
  max-width: 26.9375rem;
  min-height: 12.5625rem;
}

.badges {
  grid-area: logos;
  align-self: flex-end;
}

.sub-title {
  max-width: 27.4375rem;
  min-height: 11.6875rem;
  margin-top: 2.3125rem;
}

.benefits {
  grid-area: list;
  margin-top: 4.0625rem;
}

.sub-text {
  max-width: 31rem;
  min-height: 7.375rem;
  grid-area: sub-text;
}

.gold-button {
  grid-area: audit-btn;
  align-self: center;
  margin-top: 0.5rem;
  font-size: 1.25rem;
  width: 100%;
  max-width: 26.25rem;
  height: 4.5rem;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 769px) and (max-width: 1000px) {
  .first-section {
    grid-template-columns: 56.5% 43.5%;
    grid-template-rows: auto auto auto auto auto;
    grid-template-areas:
      'left-section logos'
      'left-section logos'
      'left-section benefits'
      'left-section benefits'
      'sub-text button';
    margin-top: 4.8125rem;
    min-height: 37.5rem;
    gap: 0;
  }

  .left-section {
    grid-area: left-section;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .sub-title {
    max-width: 85%;
  }

  .sub-text {
    grid-area: sub-text;
    max-width: 85%;
    margin-top: 3rem;
    align-self: end;
    align-content: end;
  }

  .benefits {
    grid-area: benefits;
    align-self: end;
  }

  .gold-button {
    grid-area: button;
    align-self: flex-end;
  }
}

@media screen and (max-width: 768px) {
  .first-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
  }

  .badges {
    margin-top: 4rem;
    order: -1;
  }

  .sub-heading {
    margin-top: 4rem;
    min-height: 6.875rem;
  }

  .sub-title {
    margin-top: clamp(2rem, 5vw, 3rem);
  }

  .benefits {
    margin-top: clamp(2.5rem, 5vw, 3.5rem);
  }

  .sub-text {
    margin-top: clamp(2.5rem, 6vw, 4rem);
  }

  .gold-button {
    margin-top: clamp(2.5rem, 6vw, 4rem);
  }
}

@media screen and (max-width: 375px) {
  .badges {
    margin-top: 3rem;
  }
}
</style>
