<template>
  <header class="header">
    <div class="header__container container">
      <MntnLogo />
      <HeaderNavigation class="header__navigation" />
      <button class="header__account">
        <icon name="codicon:account" mode="svg" /> Account</button
      >
    </div>
  </header>
</template>

<script setup></script>

<style lang="scss" scoped>
  .header {
    font-weight: 700;
    position: absolute;
    z-index: 10;
    top: tovw(65, 1920);
    left: 0;
    right: 0;
    &__container {
      display: grid;
      grid-template-columns: 200px 1fr 200px;
      padding: 0 20px;
      align-items: center;
      @media (min-width: $M) {
        padding: 0 50px;
      }
      @media (min-width: $XL) {
        padding: 0 80px;
      }
    }
    &__navigation {
      font-size: 18px;
    }
    &__account {
      font-size: 17px;
      display: flex;
      gap: 8px;
      align-items: center;
      justify-content: flex-end;
    }
  }
</style>
