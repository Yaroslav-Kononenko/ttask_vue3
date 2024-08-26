<script setup lang="ts">
  defineProps<{ isMobile: boolean }>();
</script>

<template>
  <section class="stem grid">
    <div class="grid__item--1 grid__item--desktop-1 logo-container">
      <img class="labor-logo" src="../../assets/laborStatisticLogo.svg" alt="Labor Statistic">
    </div>

    <div class="grid__item--desktop-1-7 accent title stem__title">
      According to the U.S. Bureau of Labor Statistics, <br v-if="!isMobile"/> STEM occupations 
      generated <br v-if="!isMobile"/> an annual mean wage of <span class="accent--green">$100,900</span>, 
      <br v-if="!isMobile"/> compared to <span class="accent--orange">$55,260</span> for non-STEM occupations.
    </div>

    <div class="statistics grid__item--desktop-8-11">
      <div class="statistics__stem box-bar">
        <span class="box-bar__title">STEM occupation</span>

        <div class="stem-line stem-line--green">
          <img class="stem-line__smile" src="../../assets/stemsmile.png" alt="Relieved smile">
          <span class="stem-line__text">$100,900/year</span>
        </div>
      </div>

      <div class="statistics__nonstem box-bar">
        <span class="box-bar__title">Non-STEM occupation</span>

        <div class="stem-line stem-line--orange">
          <img class="stem-line__smile" src="../../assets/nonstemsmile.png" alt="Relieved smile">
          <span class="stem-line__text">$55,260/year</span>
        </div>
      </div>
    </div>
  </section>  
</template>

<style scope lang="scss">
  .stem {
    padding: 24px 8px 32px;
    margin-bottom: 80px;
    background-color: #ffffff;

    @indlude ondesktop {
      padding: 80px 0 112px;
    }

    &__title {
      margin-bottom: 44px;

      @include ondesktop {
        margin-bottom: 0;
      }
    }
  
    &-line {
      display: flex;
      justify-content: end;
      align-items: center;
      height: 32px;
      text-align: right;

      &__smile {
        width: 16px;
        height: 16px;
      }

      &__text {
        padding: 8px;

        @include ondesktop {
          padding: 4px;
        }
      }

      &--green {
        color: #ffffff;
        background-color: $colorAccent-green;
      }

      &--orange {
        width: calc(55.260% / 100.900 * 100);
        color: $colorPrimary;
        background-color: $colorAccent-orange;
      }
    }
  }

  .statistics {
    display: flex;
    flex-direction: column;
    gap: 16px;


    @include ondesktop {
      justify-content: center;
      gap: 24px;
    }
  }

  .title {
    @include ondesktop {
      font-size: 24px;
      line-height: 40px;
    }
  }

  .logo-container {
    margin-bottom: 9px;

    @include ondesktop {
      margin-bottom: 24px;
    }
  }

  .labor-logo {
    @include ondesktop {
      width: 100%;
      height: 100%;
    }
  }

  .box-bar {
    &__title {
      @include ondesktop {
        margin-bottom: 24px;
      }
    }
  }
</style>
