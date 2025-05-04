<template>
  <div class="card">
    <div class="card__content">
      <b class="card__number">{{ number }}</b>
      <h2 class="card__title">{{ title }}</h2>
      <h3 class="card__subtitle chronicle">{{ subtitle }}</h3>
      <p class="card__text">
        <slot></slot>
      </p>
      <nuxt-link to="/blog" class="card__link">
        read more
        <icon class="card__link-icon" name="lets-icons:arrow-right" />
      </nuxt-link>
    </div>
    <div class="card__image-wrapper">
      <NuxtImg
        :src="`/img/content/${number}.png`"
        height="720"
        width="566"
        format="avif"
        loading="lazy"
        class="card__image"
      />
    </div>
  </div>
</template>

<script setup>
  defineProps({
    number: {
      type: String,
      default: "01",
    },
    title: {
      type: String,
      default: "Get Started",
    },
    subtitle: {
      type: String,
      default: "What level of hiker are you?",
    },
  });
</script>

<style lang="scss" scoped>
  .card {
    display: grid;
    grid-template-columns: calc((1460 - 566) / 566 * 1fr) 1fr;
    &.--reversed {
      grid-template-columns: 1fr calc((1460 - 566) / 566 * 1fr);
      .card__content {
        padding-right: 0;
        padding-left: 260px;
      }
      .card__image-wrapper {
        grid-column: 1;
        grid-row: 1;
      }
      .card__number {
        left: 110px;
      }
    }
    &__content {
      position: relative;
      padding: 140px 150px;
      padding-right: 110px;
      display: flex;
      flex-direction: column;
      gap: 27px;
    }
    &__number {
      position: absolute;
      left: 0;
      top: 35px;
      font-size: 240px;
      font-weight: 700;
      opacity: 0.1;
    }
    &__title {
      text-transform: uppercase;
      font-weight: 800;
      letter-spacing: 6px;
      color: var(--Accent, #fbd784);
      --width: 72px;
      display: flex;
      align-items: center;
      &::before {
        content: "";
        font-size: var(--width, 0);
        width: 1em;
        margin-right: em(24, 72);
        border-bottom: var(--Accent, #fbd784) solid 1px;
        border-top: var(--Accent, #fbd784) solid 1px;
      }
    }
    &__subtitle {
      font-size: em(64, 18);
      font-weight: 600;
    }
    &__text {
      font-weight: 700;
      line-height: 32px;
    }
    &__link {
      display: flex;
      align-self: flex-start;
      gap: 16px;
      color: var(--Accent, #fbd784);
      font-weight: 700;
      align-items: center;
      margin: calc(-10px - 0.25em) -10px;
      padding: 10px;
      transition: $trTime;
      &-icon {
        font-size: 1.5em;
        scale: 1.2 1;
        transform-origin: left center;
        transition: $trTime;
      }
      @include hover {
        gap: 8px;
        transition: $hoverTime;
        .card__link-icon {
          scale: 1;
          transition: $hoverTime;
        }
      }
    }
    &__image-wrapper {
      position: relative;
      padding-bottom: percent(720, 566);
    }
    &__image {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
</style>
