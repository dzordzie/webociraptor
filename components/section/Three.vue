<template>
  <section class="path-section">
    <TextWithUnderlines
      text="A Quick and Fearless Route to Web&nbsp;Dominance"
      class="path-heading"
      v-bind="pathHeading"
    />
    <div class="step-components">
      <Step
        v-for="step in steps"
        :key="step.title"
        v-bind="step"
        :boldText="boldText"
      />
    </div>
  </section>
</template>

<script setup>
const { data: steps } = await useFetch('/api/database', {
  transform: (_steps) => _steps.data.auditSteps,
})

const pathHeading = {
  underlined: ['Dominance'],
}

const boldText = [
  'specific goals',
  'sets you apart from the competition.',
  'gather precise data that will lead to optimized solutions.',
  'Analyze insights,',
  'implement improvements',
  'Deliver a final design that gives your brand a predatory advantage',
]
</script>

<style scoped>
.path-section {
  margin-top: 102px;
}

.path-heading {
  margin: 4.8125rem auto 6rem auto;
  max-width: 37.5rem;
  min-height: 10.1875rem;
  text-align: center;
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 768px) {
  .path-section {
    margin-top: clamp(6rem, 12vw, 7rem);
  }
}

@media screen and (max-width: 375px) {
  .path-heading {
    margin: 0;
    text-align: left;
  }

  .step-components {
    margin-top: 2.5rem;
  }
}
</style>
