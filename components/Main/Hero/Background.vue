<template>
  <Transition name="fade">
    <div class="bg">
      <NuxtImg
        src="/img/hero/hg.png"
        sizes="300px xs:400px sm:700px md:900px lg:1280px xl:1440px xxl:1920px"
        format="avif,webp"
        loading="eager"
        preload
        class="bg__image --hg"
        aria-hidden
        alt=""
        @load="(el) => loaded.push(el)"
        data-speed="clamp(0.3)"
      />
      <NuxtImg
        src="/img/hero/mg.png"
        width="1920"
        height="1920"
        sizes="300px xs:400px sm:700px md:900px lg:1280px xl:1440px xxl:1920px"
        format="avif,webp"
        loading="eager"
        preload
        class="bg__image --mg"
        aria-hidden
        alt=""
        @load="(el) => loaded.push(el)"
        data-speed="clamp(0.7)"
      />
      <NuxtImg
        src="/img/hero/lg.png"
        width="1920"
        height="1920"
        sizes="300px xs:400px sm:700px md:900px lg:1280px xl:1440px xxl:1920px"
        format="avif,webp"
        loading="eager"
        preload
        class="bg__image --lg"
        aria-hidden
        alt=""
        @load="(el) => loaded.push(el)"
      />
      <div class="bg__image bg__gradient--top"></div>
      <div class="bg__image bg__gradient--bottom"></div>
    </div>
  </Transition>
</template>

<script setup>
  const loaded = useState("bgLoaded", () => []);
</script>

<style lang="scss" scoped>
  .bg {
    pointer-events: none;
    overflow: hidden;
    &__image {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      &.--lg {
        z-index: 1;
      }
    }
    &__gradient--top {
      height: percent(1200, 1920);
      background: linear-gradient(
        330deg,
        rgba(11, 29, 38, 0) 31.06%,
        #0b1d26 108.93%
      );
    }
    &__gradient--bottom {
      inset: unset;
      bottom: 0px;
      left: 0;
      right: 0;
      height: percent(720, 1920);
      background: linear-gradient(
        180deg,
        rgba(11, 29, 38, 0) 0%,
        #0b1d26 61.38%
      );
      z-index: 2;
    }
  }
</style>
