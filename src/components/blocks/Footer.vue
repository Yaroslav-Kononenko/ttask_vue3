<script setup lang="ts">
  import ActionButtonComponent from '../atoms/ActionButtonComponent.vue';

  defineProps<{ isMobile: boolean }>();
</script>

<template>
  <footer class="footer">
    <div class="grid">
      <span class="title grid__item--desktop-3-10">
        Math is an essential skill to succeed. <br v-if="!isMobile"/> Check your child’s knowledge level.
      </span>
    </div>

    <div class="action-button">
      <ActionButtonComponent :isAccent=!isMobile />
    </div>

    <img class="student-img footer__girl" src="../../assets/footerGirl.webp" alt="Girl student">
    <img class="student-img footer__boy" src="../../assets/footerBoy.webp" alt="Boy student">
  </footer>
</template>

<style scoped lang="scss">
  .footer {
    position: relative;
    padding: 80px 8px 88px;
    background-color: $footerBgColor;
    text-align: center;

    &__girl {
      left: 8px;
      height: 202px;

      @include ondesktop {
        left: 75px;
        height: 300px;
      }
    }

    &__boy {
      right: 8px;
      height: 239px;

      @include ondesktop {
        right: 66px;
        height: 325px;
      }
    }
  }

  .title {
    display: inline-block;
    text-align: center;
    color: #ffffff;
    font-size: 16px;
    line-height: 24px;
    font-weight: 800;
    padding: 0 20px;
    margin-bottom: 40px;

    @include ondesktop {
      font-size: 32px;
      line-height: 48px;
    }
  }

  .student-img {
    position: absolute;
    bottom: 0;
  }

  .action-button {
    margin-bottom: 175px;

    @include ondesktop{
      margin-bottom: 0;
    }
  }  
</style>