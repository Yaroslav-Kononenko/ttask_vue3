<script setup lang="ts">
  import Card from './Card.vue';

  import card1 from '../../assets/card1.png';
  import card2 from '../../assets/card2.png';
  import card3 from '../../assets/card3.png';
  import card4 from '../../assets/card4.png';
  import card5 from '../../assets/card5.png';
  import card6 from '../../assets/card6.png';
  import TrustCarousel from './TrustCarousel.vue';

  const cards = [
    { image: card1 },
    { image: card2 },
    { image: card3 },
    { image: card4 },
    { image: card5 },
    { image: card6 },
  ];

  defineProps<{ isMobile: boolean }>();
</script>

<template>
  <div class="trust-pilots">
    <div class="title grid">
      <span class="grid__item--desktop-4-9">
        Check out our review
        from Parents like you
      </span>
    </div>

    <Card v-if="!isMobile" :cards=cards />
    <TrustCarousel v-else :cards=cards />
  </div>
</template>

<style scoped lang="scss">
  .trust-pilots {
    margin-bottom: 80px;
    padding: 0 8px;
  }

  .title {
    font-size: 16px;
    line-height: 24px;
    text-align: center;
    font-weight: 800;
    margin-bottom: 16px;

    @include ondesktop {
      text-align: left;
      font-size: 48px;
      line-height: 64px;
      margin-bottom: 40px;
    }
  }
</style>
