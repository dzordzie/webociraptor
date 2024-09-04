<template>
  <button class="gold-button" @click="handleClick">
    {{ title }}
  </button>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    default: 'I Want a Web Raptor',
  },
  clickFunction: {
    type: Function,
    required: false,
  },
})

const handleClick = () => {
  if (props.clickFunction) {
    props.clickFunction()
  }
}
</script>

<style scoped>
.gold-button {
  font-weight: 900;
  text-align: center;
  color: var(--light);
  background-color: #001d1f95;
  border-radius: 8px;
}

.gold-button:hover,
.gold-button:active {
  color: var(--dark);
  outline: 4px solid var(--dark);
  outline-offset: -4px;
  background: var(--goldGradient);
}
</style>
