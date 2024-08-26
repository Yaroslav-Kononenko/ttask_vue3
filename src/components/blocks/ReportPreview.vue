<script setup lang="ts">
  import ActionButtonComponent from '../atoms/ActionButtonComponent.vue';
  import Carousel from './Carousel.vue';

  defineProps<{ isMobile: boolean }>();
</script>

<template>
  <section class="report-prev grid">
    <div class="text-box grid__item--desktop-2-6">
      <div class="text-box__title">
        <span>We will evaluate your kid's:</span>
      </div>

      <ol class="text-box__list">
        <li>
          <span>1.</span> 
          Math knowledge overall proficiency
        </li>
        <li>
          <span>2.</span>
          Competence with Common Core Standards for Math Analysis
        </li>
        <li>
          <span>3.</span>
          The appropriate pace of learning
        </li>
        <li>
          <span>4.</span>
          Problem-solving, communication, and analytical skills
        </li>
      </ol>

      <ActionButtonComponent v-if="!isMobile" />
    </div>

    <div class="slider grid__item--desktop-7-12">
      <Carousel />
    </div>

    <div class="mobile-button" v-if="isMobile">
      <ActionButtonComponent />
    </div>
  </section>
</template>

<style lang="scss">
  .report-prev {
    margin-bottom: 80px;
    margin-left: 8px;
    margin-right: 8px;
  }

  .text-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;

    font-weight: 800;

    &__title {
      font-size: 20px;
      line-height: 28px;
      margin-bottom: 12px;

      @include ondesktop {
        font-size: 32px;
        line-height: 48px;
        margin-bottom: 16px;
      }
    }

    &__list {
      list-style: none;
      margin: 0;
      padding-left: 0;

      @include ondesktop {
        margin-bottom: 48px;
      }

      li {
        font-size: 14px;
        line-height: 24px;

        @include ondesktop {
          font-size: 16px;
          margin-bottom: 8px;

          &:last-child {
            margin-bottom: 0;
          }
        }

        & > :nth-child(n) {
          margin-right: 8px;
        }
      }
    }
  }

  .slider {
    margin-bottom: 24px;

    @include ondesktop {
      margin-bottom: 0;
    }
  }

  .mobile-button {
    text-align: center;
  }
</style>
