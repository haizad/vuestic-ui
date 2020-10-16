<template>
  <div class="preview">
    <div class="preview__wrapper">
      <div class="preview__inner">
        <div class="preview__title">Vue.js UI Library</div>
        <div class="preview__buttons">
          <va-button class="preview__buttons--button"
            :round="false"
            color="#2550C0"
          >
            Get started
          </va-button>
          <va-button class="preview__buttons--button"
            :round="false"
            color="#2550C0"
            flat icon="github"
          >
            View on GitHub
          </va-button>
        </div>
        <div class="preview__image">
        </div>
        <div class="preview__features">

          <!-- items -->
          <div class="item">
            <div class="item__frame">
              <img src="@/assets/landing/images/features/nuxt-support.png" alt="nuxt-support">
            </div>
            <h2 class="item__title">Nuxt support</h2>
            <a href="#" class="item__link">Nuxt integration guides</a>
          </div>

          <div class="item">
            <div class="item__frame">
              <img src="@/assets/landing/images/features/components.png" alt="responsive-components">
            </div>
            <h2 class="item__title">52 Responsive Components</h2>
            <a href="#" class="item__link">Available components docs</a>
          </div>

          <div class="item">
            <div class="item__frame">
              <img src="@/assets/landing/images/features/keyboard-navigation.png" alt="keyboard-navigation">
            </div>
            <h2 class="item__title">Keyboard Navigation</h2>
            <a href="#" class="item__link">Accessibility guides</a>
          </div>

          <div class="item">
            <div class="item__frame">
              <img src="@/assets/landing/images/features/modern-browsers.png" alt="modern-browsers">
            </div>
            <h2 class="item__title">Modern Browsers Support</h2>
            <a href="#" class="item__link">Supported browsers list</a>
          </div>
          <!-- /items -->
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
@Component({})
export default class Preview extends Vue {}
</script>

<style lang="scss" scoped>
@import "../../assets/main.scss";

.preview {
  width: 100%;
  position: relative;
  padding-top: 4.5rem;
  background: transparent;

  &__wrapper {
    @include wrapper();
  }

  &__inner {
    @include row-flex();

    align-items: center;
  }

  &__title {
    @include col();
    @include size(12);

    padding-top: 3.5rem;
    text-align: center;
    font-weight: 900;
    font-size: 4.5rem;
  }

  &__buttons {
    @include col();
    @include size(12);

    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: 1.5rem;

    &--button {
      height: 3rem;
      font-weight: 600;
      font-size: 1rem;
    }
  }

  &__image {
    position: absolute;
    background-image: url("../../assets/landing/images/image-components.png");
    background-size: contain;
    background-repeat: repeat-x;
    background-position: top;
    height: 342px;
    top: 20rem;
    left: 0;
    width: 100%;
    z-index: 1;
  }

  &__features {
    padding-top: 30rem;
    padding-bottom: 8rem;

    @include row-flex();
    @include col();
    @include size(12);

    justify-content: center;
  }
}

.item {
  @include col();
  @include size(3);

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &__frame {
    display: inline-block;
    padding: 0.75rem;
    border: 1px dashed $gray;
    border-radius: 1rem;
  }

  &__title {
    text-align: center;
    padding: 0.75rem 0 0.5rem;
    font-weight: 700;
    font-size: 1.4rem;
    line-height: 1.8rem;
  }

  &__link {
    text-align: center;
    font-weight: 600;
    line-height: 1.6rem;
    font-size: 1rem;
  }
}
</style>