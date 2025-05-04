<template>
  <nav class="navigation">
    <ul class="navigation__list">
      <li class="navigation__li">
        <nuxt-link to="/equipment" class="navigation__link"
          >Equipment</nuxt-link
        >
      </li>
      <li class="navigation__li">
        <nuxt-link to="/about" class="navigation__link">About us</nuxt-link>
      </li>
      <li class="navigation__li">
        <nuxt-link to="/blog" class="navigation__link">Blog</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script setup></script>

<style lang="scss" scoped>
  .navigation {
    &__list {
      display: flex;
      justify-content: center;
      gap: 40px;
    }
    &__li {
    }
    &__link {
    }
  }
</style>
