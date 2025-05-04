<template>
  <Main class="main">
    <MainHero class="main__hero" />
  </Main>
</template>

<style lang="scss" scoped>
  .main {
    flex: 1;
  }
</style>

<script setup>
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { ScrollSmoother } from "gsap/ScrollSmoother";

  definePageMeta({ layout: "custom" });

  gsap.registerPlugin(ScrollTrigger, ScrollSmoother);
  onMounted(() => {
    ScrollSmoother.create({
      smooth: 1, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
      smoothTouch: 0.1, // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)
    });
  });
</script>
