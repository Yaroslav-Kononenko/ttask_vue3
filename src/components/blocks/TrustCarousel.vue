<script setup lang="ts">
  import { Pagination, EffectCoverflow } from 'swiper/modules';
  import { Swiper, SwiperSlide } from 'swiper/vue';

  import 'swiper/css';
  import 'swiper/css/pagination';
  import 'swiper/css/effect-coverflow';
  
  interface Card {
    image: string;
  }

  defineProps<{ cards: Card[] }>();
</script>

<template>
  <swiper
    :modules="[Pagination, EffectCoverflow]"
    :slides-per-view="1"
    :space-between="50"
    navigation
    loop
    :pagination="{ el: '.custom-pag', clickable: true }"
    :scrollbar="{ draggable: true }"
    :coverflowEffect="{
      rotate: 0,
      stretch: 0,
      depth: 250,
      modifier: 1,
      slideShadows: false,
    }"
  >
    <swiper-slide v-for="(card, index) in cards" :key="index">
      <img class="slide-img" :src=card.image alt="slide">
    </swiper-slide>
    <div class="custom-pag" />
  </swiper>
</template>

<style lang="scss">
  .custom-pag {
    position: relative;
    margin-top: 16px;
    z-index: 999;
    text-align: center;

    .swiper-pagination-bullet {
      width: 8px;
      height: 8px;
      border: 2px solid $colorPrimary;
      background-color: $mainBgColor;
      opacity: 1;
      margin: 0 4px;
    }

    .swiper-pagination-bullet-active {
      border-radius: 50%;
      background: $paginationColor--active;
    }
  }

  .slide-img {
    width: 100%;
    object-fit: cover;
  }
</style>
