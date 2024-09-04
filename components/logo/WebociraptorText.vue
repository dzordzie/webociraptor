<template>
  <img
    class="logo-text"
    src="~/assets/svg/logo-webociraptor.svg"
    alt="riesenia"
  />
</template>

<style scoped>
.logo-text {
  height: 3rem;
  width: auto;
}

/* =================== RESPONSIVE ======================= */

@media screen and (min-width: 376px) and (max-width: 768px) {
  .logo-text {
    height: clamp(1.5rem, 6.25vw, 3rem);
    width: auto;
  }
}

@media screen and (max-width: 375px) {
  .logo-text {
    height: 1.5rem;
    width: auto;
  }
}
</style>
