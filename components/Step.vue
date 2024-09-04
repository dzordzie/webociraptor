<template>
  <div class="path-step">
    <img class="number-image" :src="numberImage" alt="number" />
    <div class="step-info">
      <h3 class="step-title">
        {{ title }}
      </h3>
      <TextWithBolds
        :text="text"
        :boldText="boldText"
        :sizeClass="'size-16px'"
      />
    </div>
    <img class="arrow-image" src="/svg/arrow.svg" alt="arrow" />
  </div>
</template>

<script setup>
const props = defineProps({
  numberImage: String,
  title: String,
  text: String,
  boldText: Array,
})
</script>

<style scoped>
.path-step {
  display: flex;
  width: 100%;
  flex-direction: row;
  padding: 0 1rem;
  margin-top: 2.5rem;
}

.step-info {
  margin-left: 2.375rem;
  width: 22.8125rem;
}

.path-step:nth-child(2n) .step-info {
  width: 23.375rem;
}

.path-step:nth-child(2n) {
  justify-content: flex-end;
}

.number-image {
  height: 110px;
  width: auto;
}

.step-title {
  font-size: 1.5rem;
  font-weight: 900;
  line-height: 1.875rem;
  text-align: left;
  text-shadow: 1px 1px 2px black;
}

.arrow-image {
  height: 4.625rem;
  width: auto;
  margin-top: 3rem;
  margin-left: 2rem;
}

.path-step:nth-child(2n) .arrow-image {
  transform: scaleX(-1);
  order: -1;
  margin-left: 0;
  margin-right: 2rem;
}

.path-step:last-child .arrow-image {
  display: none;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 376px) and (max-width: 768px) {
  .path-step {
    padding: 0;
    text-align: center;
    margin-top: 4rem;
  }

  .arrow-image {
    display: none;
  }

  .number-image {
    margin-bottom: 1.5rem;
  }
}

@media screen and (max-width: 375px) {
  .path-step {
    padding: 0;
    height: 8.75rem;
    margin-top: 3.4375rem;
    position: relative;
  }

  .path-step:first-child {
    margin-top: 0;
  }

  .arrow-image {
    display: none;
  }

  .step-info {
    position: absolute;
    width: 13.5rem;
    left: 0;
    margin-left: 5.375rem;
  }

  .path-step:nth-child(2n) .step-info {
    width: 190px;
  }

  .path-step:nth-child(2n) {
    justify-content: flex-start;
  }

  .step-title {
    width: 100%;
    margin-bottom: 0.3125rem;
  }

  .number-image {
    height: 4.5rem;
    margin-bottom: 0;
    margin-top: 1.5rem;
  }
}
</style>
