<template>
  <h1 class="heading">{{ title }}</h1>
</template>

<script setup>
const props = defineProps({
  title: String,
})
</script>

<style scoped>
.heading {
  width: 100%;
  color: var(--light);
  font-weight: 300;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: auto;
  margin-right: auto;
  text-shadow: 2px 2px 2px black;
}
</style>
