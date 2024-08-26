<script setup lang="ts">
  import ActionButtonComponent from '../atoms/ActionButtonComponent.vue';
</script>

<template>
  <section class="better-greater grid">
    <div class="better-greater__info grid__item--desktop-4-8">
      <div class="info">
        The better your child <span class="accent--green">knows math</span>,
        the greater the probability
        that they will manage to get a STEM
        profession and <span class="accent--green">earn more</span> in the future.
      </div>

      <ActionButtonComponent />
    </div>
  </section>
</template>

<style scoped lang="scss">
  .better-greater {
    background-color: #ffffff;
    padding: 24px 8px 32px;
    margin-bottom: 80px;
    
    @include ondesktop {
      padding: 64px 0 68px;
    }

    &__info {
      display: flex;
      flex-direction: column;
      align-items: center;

      @include ondesktop {
        align-items: start;
      }
    }
  }

  .info {
    font-size: 14px;
    line-height: 20px;
    font-weight: 800;
    margin-bottom: 16px;

    @include ondesktop {
      font-size: 24px;
      line-height: 40px;
      margin-bottom: 32px;
    }
  }
</style>