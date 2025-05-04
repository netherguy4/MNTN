<template>
  <!-- <Overlay /> -->
  <div id="smooth-wrapper">
    <div class="wrapper" id="smooth-content">
      <Header class="wrapper__header" data-lag="1" />
      <slot />
      <Footer class="wrapper__footer" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    &__header {
      position: absolute;
      z-index: 10;
      top: 65px;
      left: 0;
      right: 0;
    }
  }
</style>
