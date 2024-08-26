<script setup lang="ts">
  import logo1 from '../../assets/AP logo.svg';
  import logo2 from '../../assets/MarketWatch.svg';
  import logo3 from '../../assets/Markets Insider.svg';
  import logo4 from '../../assets/Yahoo finance.svg';
  import logo5 from '../../assets/Homeschool.svg';

  const logosTop = [
    {img: logo1, alt: 'AP_logo'},
    {img: logo2, alt: 'MarketWatch'},
  ];
  
  const logosBottom = [
    {img: logo3, alt: 'Markets Insider'},
    {img: logo4, alt: 'Yahoo finance'},
    {img: logo5, alt: 'Homeschool'}
  ]
  
  const logos = [...logosTop,...logosBottom];
  
  defineProps<{ isMobile: boolean }>();
</script>

<template>
  <div class="featuredin">
    <div class="title">
      Featured In
    </div>

    <div class="grid">
      <div class="logos grid__item--desktop-3-10">
        <div class="logos__container">
          <div v-for="(logo, index) in isMobile ? logosTop : logos" :key="index">
            <img class="logo" :src="logo.img" :alt="logo.alt">
          </div>
        </div>

        <div class="logos__container" v-if="isMobile">
          <div v-for="(logo, index) in logosBottom" :key="index">
            <img class="logo" :src="logo.img" :alt="logo.alt">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .featuredin {
    padding: 24px 8px 40px;
    background-color: #ffffff;

    @include ondesktop {
      font-weight: 600;
      padding-top: 56px;
      padding-bottom: 63px;
    }
  }

  .title {
    margin-bottom: 16px;
    text-align: center;
    font-size: 16px;
    line-height: 24px;
    font-weight: 800;

    @include ondesktop {
      font-size: 48px;
      line-height: 64px;
      margin-bottom: 31px;
      font-weight: 600;
    }
  }

  .logos {
    &__container {
      display: flex;
      justify-content: center;

      &:first-child {
        margin-bottom: 17px;

        @include ondesktop {
          width: -webkit-fill-available;
          justify-content: space-between;
        }
      }

      &:last-child {
        justify-content: space-between;

        .logo {
          width: inherit;
        }
      }
    }
  }

</style>
