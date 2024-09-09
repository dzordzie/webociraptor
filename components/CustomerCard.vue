<template>
  <div class="customer-card">
    <div class="customer-wrap">
      <img
        class="quotation-marks"
        src="/svg/quotation-marks.svg"
        alt="quotes"
      />
      <p class="customers-words">
        {{ isExpanded ? text : shortText }}

        <span class="show-text" @click="toggleText">{{
          isExpanded ? 'show less ▲' : 'show more ▼'
        }}</span>
      </p>
    </div>
    <div class="customers-sign">
      <img class="customers-logo" :src="logo" alt="logo" />
      <div class="customers-info">
        <h4 class="customers-name">{{ name }}</h4>
        <p>
          {{ position }}
          <a class="red-text company" :href="web">{{ company }}</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  text: String,
  name: String,
  position: String,
  company: String,
  logo: String,
  web: String,
})

const isExpanded = ref(false)
const maxLength = 320
const shortText = computed(() => {
  return props.text.length > maxLength
    ? props.text.slice(0, maxLength) + ' ...'
    : props.text
})
const toggleText = () => {
  isExpanded.value = !isExpanded.value
}
</script>

<style scoped>
.customer-card {
  width: 100%;
  max-width: 29rem;
  font-size: 1.125rem;
  line-height: 2rem;
  text-align: left;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  text-shadow: 1px 2px 2px black;
}

.customer-wrap {
  width: 100%;
  min-height: 17.75rem;
  border: 1px solid var(--outline);
  box-sizing: border-box;
  position: relative;
}

.customers-words {
  width: 85%;
  min-height: 14rem;
  font-weight: 400;
  margin: 2.25rem;
  display: flex;
  flex-direction: column;
}

.customers-sign {
  display: flex;
  align-items: center;
  height: 4.0625rem;
  margin-top: 2.125rem;
}

.customers-info {
  line-height: 1.375rem;
  margin-left: 1.1875rem;
}

.customers-logo {
  height: 4rem;
  width: auto;
}

.customers-name {
  font-weight: 900;
}

.quotation-marks {
  position: absolute;
  top: -1.5rem;
  left: 1.875rem;
  filter: drop-shadow(2px 2px 3px rgba(0, 0, 0, 0.5));
}

.show-text {
  font-weight: 900;
  color: rgb(255, 217, 214);
  cursor: pointer;
  font-style: italic;
  align-self: flex-end;
  justify-self: flex-end;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 376px) and (max-width: 768px) {
  .customer-card {
    margin-bottom: 7.5rem;
  }

  .customer-card:last-child {
    margin-bottom: 0;
  }
}

@media screen and (max-width: 375px) {
  .customer-card {
    margin-bottom: 4.75rem;
  }

  .customer-card:last-child {
    margin-bottom: 0;
  }

  .customer-wrap {
    width: 20.1875rem;
    min-height: 22.5rem;
  }

  .customers-words {
    width: 17.25rem;
    height: auto;
    align-content: center;
    margin: 1.75rem auto auto auto;
  }

  .customer-card:last-child .customers-words {
    width: 16.4375rem;
  }

  .customers-sign {
    margin-top: 1.5rem;
  }

  .customers-info {
    line-height: 1.375rem;
    margin-left: 1.1875rem;
  }

  .quotation-marks {
    left: 1.6875rem;
  }
}
</style>
