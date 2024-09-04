<template>
  <div class="logo-full">
    <img
      src="/svg/text-webociraptor.svg"
      alt="webociraptor"
      class="webocitext"
    />
    <img
      src="/svg/stopy-webociraptor.svg"
      alt="webociraptor"
      class="webocistopy"
    />
  </div>
</template>

<style scoped>
.logo-full {
  position: relative;
  width: 100rem;
  height: auto;
  align-self: center;
}

.webocistopy {
  position: absolute;
  width: 75%;
  height: auto;
  top: 0;
  left: 0;
}

.webocitext {
  position: relative;
  width: 75%;
  height: auto;
  z-index: 1;
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 1024px) {
  .logo-full {
    width: clamp(40rem, 156vw, 100rem);
  }
}
</style>
