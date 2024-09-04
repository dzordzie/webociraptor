<template>
  <h2 class="underlined-text" v-html="editedText"></h2>
</template>

<script setup>
const props = defineProps({
  text: String,
  underlined: Array,
})

const editedText = computed(() => {
  const underlinedStrings = props.underlined
  let normalText = props.text
  underlinedStrings.forEach((str) => {
    if (underlinedStrings.length === 0) {
      return normalText
    }
    const regex = new RegExp(`(${str})`, 'g')
    normalText = normalText.replace(
      regex,
      `<span class="underlined-word">$1</span>`
    )
  })
  return normalText
})
</script>

<style>
.underlined-text {
  font-size: 3rem;
  font-weight: 700;
  line-height: 4rem;
  text-align: left;
  text-shadow: 2px 2px 3px black;
}

.underlined-word {
  position: relative;
  text-shadow: 2px 2px 3px black;
  z-index: 1;
  white-space: nowrap;
}

.underlined-word::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0rem;
  width: 100%;
  height: 0.875rem;
  background: var(--goldGradient);
  z-index: -1;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 376px) and (max-width: 768px) {
  .underlined-text {
    font-size: clamp(2rem, 6vw, 2.6rem);
    line-height: clamp(2.75rem, 7vw, 4rem);
  }
}

@media screen and (max-width: 375px) {
  .underlined-text {
    font-size: 2rem;
    line-height: 2.75rem;
  }

  .underlined-word {
    text-decoration: solid underline var(--underline) 0.875rem;
    text-underline-offset: 0.25rem;
    text-decoration-skip-ink: none;
  }
}
</style>
