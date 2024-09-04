<template>
  <header class="header-component">
    <img src="../assets/img/jungle.png" class="left-leafs" />
    <img src="../assets/img/jungle.png" class="right-leafs" />
    <div class="header-wrapper">
      <GoldButton :clickFunction="show" />
      <LogoWebociraptorFull />
      <TextHeading title="The Raptor for Your Website." />
      <ContactForm ref="dialogTarget" />
    </div>
  </header>
</template>

<script setup>
const dialogTarget = ref(null)
const show = () => dialogTarget.value?.show()
</script>

<style scoped>
.header-component {
  width: 100%;
  height: 35rem;
  background: var(--backgroudn-dark);
}

.header-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.left-leafs {
  position: fixed;
  top: -5rem;
  left: 0;
  height: 38vw;
  width: auto;
  z-index: 1;
  opacity: 0.8;
}

.right-leafs {
  position: fixed;
  top: -5rem;
  right: 0;
  height: 38vw;
  width: auto;
  z-index: 1;
  transform: scale(-1, 1);
  opacity: 0.8;
}

.logo-full {
  top: -26.5px;
  z-index: 0;
}

.gold-button {
  position: absolute;
  font-size: 1rem;
  width: 17rem;
  height: 3rem;
  margin-top: 3.5rem;
  align-self: flex-end;
  margin-right: 10rem;
  z-index: 1;
}

.heading {
  font-size: 2rem;
  margin-top: -8rem;
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 1360px) {
  .left-leafs,
  .right-leafs {
    display: none;
  }
}

@media screen and (max-width: 1150px) {
  .gold-button {
    position: static;
    align-self: center;
    order: 3;
    margin-right: 0;
  }
}

@media screen and (max-width: 1024px) {
  .header-component {
    height: clamp(20rem, 55vw, 35rem);
  }

  .heading {
    font-size: clamp(1.25rem, 3.125vw, 2rem);
    margin-top: clamp(-8rem, -12vw, -4rem);
  }

  .logo-full {
    top: clamp(-26.5px, -2.6vw, -15px);
  }

  .gold-button {
    margin-top: clamp(2rem, 5.5vw, 3.5rem);
  }
}

@media screen and (max-width: 768px) {
  .header-wrapper {
    margin: 0 auto;
    display: flex;
    flex-direction: column;
  }
}

@media screen and (max-width: 375px) {
  .gold-button {
    margin-top: 3rem;
    font-size: 0.875rem;
    width: 15rem;
    height: 2.5rem;
  }
}
</style>
