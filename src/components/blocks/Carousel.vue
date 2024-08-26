<script setup>
  import { Pagination, EffectCoverflow } from 'swiper/modules';

  import { Swiper, SwiperSlide } from 'swiper/vue';

  import 'swiper/css';
  import 'swiper/css/pagination';
  import 'swiper/css/effect-coverflow';
  import slide1 from '../../assets/slide1.webp';
  import slide2 from '../../assets/slide2.webp';
  import slide3 from '../../assets/slide3.webp';
  import slide4 from '../../assets/slide4.webp';
  import slide5 from '../../assets/slide5.webp';

  const slides = [slide1, slide2, slide3, slide4, slide5];

  const onSwiper = (swiper) => {
    console.log(swiper);
  };
  const onSlideChange = () => {
    console.log('slide change');
  };

</script>

<template>
  <swiper
    :modules="[Pagination, EffectCoverflow]"
    :slides-per-view="1"
    :space-between="50"
    navigation
    loop
    :pagination="{ el: '.custom-pagination', clickable: true }"
    :scrollbar="{ draggable: true }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
    :coverflowEffect="{
      rotate: 0,
      stretch: 0,
      depth: 250,
      modifier: 1,
      slideShadows: false,
    }"
  >
    <swiper-slide v-for="(slide, index) in slides" :key="index">
      <img class="slide-img" :src="slide" alt="slide">
    </swiper-slide>
    <div class="custom-pagination" />
  </swiper>
</template>

<style lang="scss">
  .custom-pagination {
    position: relative;
    margin-top: 8px;
    z-index: 999;
    text-align: center;

    @include ondesktop {
      margin-top: 16px;
    }

    .swiper-pagination-bullet {
      width: 8px;
      height: 8px;
      background: $paginationColor;
      opacity: 1;
      margin: 0 4px;
    }

    .swiper-pagination-bullet-active {
      background: $paginationColor--active;
      width: 56px;
      border-radius: 4px;
    }
  }

  .slide-img {
    width: 100%;
    object-fit: cover;
  }
</style>
