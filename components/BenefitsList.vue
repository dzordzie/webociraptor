<template>
  <div class="benefits">
    <ul class="benefits-list">
      <li
        class="benefit-item"
        v-for="benefit in selectedBenefits"
        :key="benefit.text"
      >
        <span class="check-mark"></span>
        {{ benefit.text }}
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  start: Number,
  end: Number,
})

const { data: benefits } = await useFetch('/api/database', {
  transform: (_benefits) => _benefits.data.benefits,
})

const selectedBenefits = computed(() => {
  return benefits.value.slice(props.start, props.end)
})
</script>

<style scoped>
.benefits-list {
  display: flex;
  flex-direction: column;
  text-shadow: 2px 2px 2px black;
  height: 100%;
}

.benefit-item {
  list-style: none;
  margin: 0;
  margin-top: 1rem;
  font-size: 1.125rem;
  font-weight: 600;
  line-height: 2.1875rem;
  text-align: left;
  display: flex;
  align-items: center;
}

.benefit-item:nth-child(even) {
  margin-left: 1rem;
}

.check-mark {
  height: 2rem;
  width: 2rem;
  margin-right: 1rem;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.benefit-item:nth-child(odd) .check-mark {
  background-image: url('~/assets/svg/footprint-left.svg');
}

.benefit-item:nth-child(even) .check-mark {
  background-image: url('~/assets/svg/footprint-right.svg');
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 769px) and (max-width: 1000px) {
  .benefit-item {
    margin-top: 0.5rem;
    font-size: clamp(1rem, 1.8vw, 1.125rem);
    line-height: clamp(1.875rem, 3.5vw, 2.1875rem);
  }
}

@media screen and (min-width: 376px) and (max-width: 768px) {
  .benefit-item {
    font-size: 1.0625rem;
    align-items: flex-start;
  }

  .check-mark {
    margin-right: 1rem;
    margin-top: 0.5rem;
  }
}

@media screen and (max-width: 375px) {
  .benefit-item {
    line-height: 1.6875rem;
    align-items: flex-start;
  }

  .check-mark {
    margin-right: 1.375rem;
    margin-top: 0.3125rem;
  }
}
</style>
