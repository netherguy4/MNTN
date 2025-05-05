<template>
  <div id="smooth-wrapper">
    <div class="wrapper" id="smooth-content">
      <Header class="wrapper__header" />
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
</style>
