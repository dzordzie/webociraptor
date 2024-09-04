<template>
  <section class="customers-section">
    <CustomerCard v-for="cust in customers" :key="cust.name" v-bind="cust" />
  </section>
</template>

<script setup>
const { data: customers } = await useFetch('/api/database', {
  transform: (_customers) => _customers.data.customers,
})
</script>

<style scoped>
.customers-section {
  display: flex;
  gap: 0 3vw;
  justify-content: space-between;
  margin-top: 8.125rem;
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 768px) {
  .customers-section {
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
