<template>
  <p class="highlighted-text" :class="sizeClass" v-html="editedText"></p>
</template>

<script setup>
const props = defineProps({
  text: String,
  boldText: Array,
  sizeClass: String,
})

const editedText = computed(() => {
  const boldStrings = props.boldText
  let normalText = props.text
  boldStrings.forEach((str) => {
    if (boldStrings.length === 0) {
      return normalText
    }
    const regex = new RegExp(`(${str})`, 'g')
    normalText = normalText.replace(regex, `<span class="bold-text">$1</span>`)
  })
  return normalText
})
</script>

<style>
.highlighted-text {
  text-align: left;
  align-content: center;
  font-weight: 400;
}

.size-16px {
  font-size: 1rem;
  line-height: 1.75rem;
  text-shadow: 1px 1px 2px black;
}

.size-16px .bold-text {
  font-weight: 700;
}

.size-22px {
  font-size: 1.375rem;
  line-height: 2.5rem;
  text-shadow: 1px 1px 2px black;
}
.size-24px {
  font-size: 1.5rem;
  line-height: 2.5rem;
  text-shadow: 2px 2px 3px black;
}

.size-26px {
  font-size: 1.625rem;
  line-height: 2.5rem;
  text-shadow: 2px 2px 3px black;
}

.bold-text {
  font-weight: 800;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 769px) and (max-width: 1000px) {
  .size-22px {
    font-size: clamp(1.125rem, 2.2vw, 1.375rem);
  }
  .size-24px {
    font-size: clamp(1.25rem, 2.4vw, 1.5rem);
  }

  .size-26px {
    font-size: clamp(1.375rem, 2.6vw, 1.625rem);
  }
}

@media screen and (min-width: 376px) and (max-width: 768px) {
  .size-22px {
    font-size: clamp(1.25rem, 2.2vw, 1.375rem);
  }

  .size-24px {
    font-size: clamp(1.25rem, 2.4vw, 1.5rem);
  }
}

@media screen and (max-width: 375px) {
  .size-24px {
    font-size: 1.25rem;
  }

  .size-26px {
    font-size: 1.375rem;
  }

  .break-line {
    display: none;
  }
}
</style>
