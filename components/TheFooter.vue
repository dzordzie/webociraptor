<template>
  <footer class="footer-component">
    <TextHeading title="Have Questions?" />
    <div class="contact-info">
      <a class="phone" href="tel:+421(05)77781888">+421(05) 777 81 888</a>
      <a class="mail" href="mailto:wrrr@webociraptor.com"
        >wrrr@webociraptor.com</a
      >
    </div>
    <LogoWebociraptorText id="logo" />
    <img src="../assets/img/jungle2.png" class="bottom-leafs" />
    <div id="running-dino">
      <img src="../assets/svg/velo-standing.svg" id="bouncing-dino" />
    </div>
  </footer>
</template>

<script setup>
const isScrolledToLogo = ref(false)

onMounted(() => {
  const logo = document.getElementById('logo')
  const image = document.getElementById('running-dino')

  window.addEventListener('scroll', () => {
    const logoPosition = logo.getBoundingClientRect().top

    if (logoPosition <= window.innerHeight && !isScrolledToLogo.value) {
      isScrolledToLogo.value = true
      image.classList.add('run')
    }
  })
})
</script>

<style scoped>
.footer-component {
  width: 100%;
  height: 48rem;
  background: var(--backgroudn-dark);
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.contact-info {
  width: 100%;
  max-width: 42.75rem;
  height: 2.5rem;
  font-size: 1.875rem;
  font-weight: 700;
  line-height: 2.5rem;
  margin-top: 4rem;
  display: flex;
  justify-content: space-between;
  text-shadow: 2px 2px 3px black;
}

.heading {
  font-size: 3rem;
  line-height: 3.6875rem;
  margin-top: 5rem;
}

.phone {
  color: var(--light);
}

.mail {
  color: var(--pinkish);
}

.logo-text {
  margin-top: 5rem;
  z-index: 2;
}

.bottom-leafs {
  position: absolute;
  width: 100%;
  height: auto;
  bottom: -5rem;
  z-index: 1;
}

@keyframes vertical-bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

#running-dino {
  position: absolute;
  bottom: -3rem;
  right: -100%;
  transition: transform 2.5s ease-in-out;
}

#bouncing-dino {
  height: 500px;
  width: auto;
  filter: blur(8px);
  animation: vertical-bounce 0.15s infinite ease-in-out;
}

.run {
  transform: translateX(calc(-200vw - 100%)) translateY(0);
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 1600px) {
  .footer-component {
    height: clamp(26rem, 48vw, 48rem);
  }

  .bottom-leafs {
    bottom: clamp(-3rem, -6vw, -5rem);
  }

  @keyframes vertical-bounce {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-15px);
    }
  }

  #running-dino {
    bottom: -3rem;
  }

  #bouncing-dino {
    height: clamp(130px, 31vw, 500px);
    width: auto;
  }
}

@media screen and (max-width: 768px) {
  .heading {
    font-size: clamp(2rem, 6vw, 3rem);
    line-height: clamp(2.5rem, 13vw, 3.5rem);
    margin-top: clamp(2.5rem, 12vw, 5rem);
    max-width: 80%;
  }

  .contact-info {
    text-align: center;
    display: flex;
    flex-direction: column;
    font-size: clamp(1.125rem, 3vw, 1.875rem);
    height: auto;
    max-height: 8rem;
    margin-top: clamp(1.5rem, 7vw, 4rem);
  }

  .logo-text {
    margin-top: clamp(3rem, 8vw, 4rem);
  }

  @keyframes vertical-bounce {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-10px);
    }
  }

  #bouncing-dino {
    transition: transform 1.5s ease-in-out;
    filter: blur(6px);
  }
}

@media screen and (max-width: 375px) {
  .footer-component {
    width: 100%;
    height: 20rem;
  }

  .heading {
    font-size: 1.5rem;
    line-height: 2.125rem;
    margin-top: 2.5rem;
  }

  .contact-info {
    font-weight: 500;
    line-height: 2rem;
  }

  .bottom-leafs {
    bottom: -8%;
  }

  #bouncing-dino {
    transition: transform 0.5s ease-in-out;
    filter: blur(4px);
  }
}
</style>
