<template>
  <div class="badges">
    <img class="badge" src="~/assets/img/no1-winner.png" />
    <img class="badge premium" src="~/assets/img/premium-choice.png" />
    <img class="badge" src="~/assets/img/satisfaction-guarantee.png" />
  </div>
</template>

<style scoped>
.badges {
  display: flex;
  width: 100%;
  height: 5.625rem;
  align-items: baseline;
}

.badge {
  height: 77%;
  width: auto;
}

.premium {
  height: 100%;
  width: auto;
  margin: 0 0.5rem;
}

/* =================== RESPONSIVE ======================= */
@media screen and (max-width: 1000px) {
  .badges {
    height: clamp(4.375rem, 9vw, 5.625rem);
  }
}

@media screen and (max-width: 768px) {
  .badges {
    height: 5.625rem;
    justify-content: center;
  }
}

@media screen and (max-width: 768px) {
  .badges {
    height: clamp(4.375rem, 9vw, 5.625rem);
  }
}
</style>
