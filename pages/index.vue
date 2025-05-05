<template>
  <Main class="main">
    <MainHero class="main__hero" />
    <MainContent class="main__content" />
  </Main>
</template>

<style lang="scss" scoped>
  .main {
    flex: 1;
    &__content {
      margin: -400px 0 0;
      position: relative;
      z-index: 2;
      background: linear-gradient(
        180deg,
        rgba(11, 29, 38, 0) 0%,
        #0b1d26 9.38%
      );
    }
  }
</style>

<script setup>
  import { gsap } from "gsap";
  import { ScrollTrigger, ScrollSmoother } from "gsap/all";

  definePageMeta({ layout: "custom" });

  gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

  const ScrollSmootherInstance = useState("ssinstance", () => undefined);
  const ScrollTriggerInstances = useState("stinstances", () => new Array());

  const init = () => {
    ScrollSmootherInstance.value = ScrollSmoother.create({
      smooth: 1, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
    });

    const target = document.querySelectorAll(".card");
    target.forEach((el, index) => {
      const id = `card${index + 1}`;
      gsap
        .timeline({
          scrollTrigger: {
            trigger: el,
            id: id,
            scrub: 1,
            start: "+=200 bottom",
            end: "90% bottom",
          },
        })
        .fromTo(el, { y: 100, autoAlpha: 0 }, { y: 0, autoAlpha: 1 });
      ScrollTriggerInstances.value.push(ScrollTrigger.getById(id));
    });
  };
  const destroy = () => {
    ScrollSmootherInstance.value ? ScrollSmootherInstance.value.kill() : "";
    ScrollTriggerInstances.value.length > 0
      ? ScrollTriggerInstances.value.forEach((trigger) => trigger.kill())
      : "";
    ScrollTriggerInstances.value = new Array();
  };

  onMounted(() => nextTick(init()));
  onBeforeUnmount(destroy);
</script>
