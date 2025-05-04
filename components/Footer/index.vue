<template>
  <footer class="footer">
    <div class="footer__container container">
      <div class="footer__content">
        <MntnLogo />
        <p class="footer__text"
          >Get out there & discover your next slope, mountain & destination!</p
        >
        <p class="footer__copy">Copyright 2019 MNTN, Inc. Terms & Privacy</p>
      </div>
      <div class="footer__content">
        <div class="footer__heading">More on The Blog</div>
        <ul class="footer__list">
          <li class="footer__li"><nuxt-link to="/">About MNTN</nuxt-link></li>
          <li class="footer__li"
            ><nuxt-link to="/">Contributors & Writers</nuxt-link></li
          >
          <li class="footer__li"><nuxt-link to="/">Write For Us</nuxt-link></li>
          <li class="footer__li"><nuxt-link to="/">Contact Us</nuxt-link></li>
          <li class="footer__li"
            ><nuxt-link to="/">Privacy Policy</nuxt-link></li
          >
        </ul>
      </div>
      <div class="footer__content">
        <div class="footer__heading">More on MNTN</div>
        <ul class="footer__list">
          <li class="footer__li"><nuxt-link to="/">The Team</nuxt-link></li>
          <li class="footer__li"><nuxt-link to="/">Jobs</nuxt-link></li>
          <li class="footer__li"><nuxt-link to="/">Press</nuxt-link></li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script setup></script>

<style lang="scss" scoped>
  .footer {
    font-size: 18px;
    line-height: 32px;
    &__container {
      display: grid;
      grid-template-columns: 1fr auto auto;
      column-gap: tovw(120, 1920);
      padding-bottom: 120px;
    }
    &__content {
      display: flex;
      flex-direction: column;
      gap: 24px;
    }
    &__text {
      font-weight: 700;
      flex: 1;
      max-width: em(303, 18);
    }
    &__copy {
      opacity: 0.5;
    }
    &__heading {
      color: var(--Accent, #fbd784);
      font-weight: 700;
      font-size: 24px;
    }
    &__list {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
  }
</style>
