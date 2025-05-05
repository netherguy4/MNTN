<template>
  <section class="hero">
    <div class="hero__container" data-speed="clamp(0.8)">
      <h1 class="hero__title">A hiking guide</h1>
      <h2 class="hero__subtitle chronicle"
        >Be prepared for the Mountains and beyond!</h2
      >
      <p class="hero__hint">
        scroll down <SvgoArrowDown class="hero__hint-arrow" />
      </p>
    </div>
    <MainHeroBackground class="hero__background" />
  </section>
</template>

<script setup>
  import { gsap } from "gsap";

  const bgLoaded = useState("bgLoaded");
  const init = () => {
    const tl = gsap.timeline();
    tl.to(".hero__background", { autoAlpha: 1 })
      .fromTo(
        ".hero__subtitle",
        {
          y: 100,
        },
        {
          y: 0,
          autoAlpha: 1,
        }
      )
      .to(".hero__title", {
        autoAlpha: 1,
      })
      .fromTo(
        ".hero__title",
        {
          "--width": 0,
        },
        {
          "--width": "72px",
          ease: "back",
        },
        "-=0.4"
      )
      .fromTo(
        ".hero__hint",
        {
          y: 50,
        },
        {
          y: 0,
          autoAlpha: 1,
        },
        "-=0.2"
      )
      .fromTo(
        ".hero__hint-arrow",
        {
          y: -5,
        },
        { y: 10, repeat: -1, yoyo: true, duration: 0.7 },
        "<"
      );
  };

  watch(
    bgLoaded,
    (arr) => {
      if (arr.length >= 3) {
        init();
      }
    },
    { deep: true }
  );
</script>

<style lang="scss" scoped>
  .hero {
    aspect-ratio: 1;
    font-size: 18px;
    position: relative;
    &__container {
      position: relative;
      z-index: 1;
      padding: tovw(290, 1920) 20px 0;
      max-width: 950px;
      margin: 0 auto;
      @media (min-width: $M) {
        padding: tovw(290, 1920) 50px 0;
        max-width: 1050px;
      }
    }
    &__title {
      visibility: hidden;
      --width: 72px;
      font-weight: 800;
      letter-spacing: 6px;
      text-transform: uppercase;
      color: var(--Accent, #fbd784);
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      @media (min-width: $M) {
        margin-bottom: 32px;
      }
      &::before {
        content: "";
        font-size: var(--width, 0);
        width: 1em;
        margin-right: em(32, 72);
        border-bottom: var(--Accent, #fbd784) solid 1px;
        border-top: var(--Accent, #fbd784) solid 1px;
      }
    }
    &__subtitle {
      visibility: hidden;
      font-weight: 600;
      font-size: 88px;
      line-height: 113%;
      text-transform: capitalize;
      margin-bottom: 16px;
      @include adaptiv-font(88, 30);
      @media (min-width: $M) {
        margin-bottom: 32px;
      }
    }
    &__hint {
      visibility: hidden;
      font-weight: 700;
      display: flex;
      gap: 16px;
      align-items: center;
    }
    &__hint-arrow {
      font-size: 24px;
    }
    &__background {
      position: absolute;
      visibility: hidden;
      inset: 0;
    }
  }
</style>
