<script setup lang="ts">
  import Header from './components/blocks/Header.vue';
  import FirstScreen from './components/blocks/FirstScreen.vue';
  import Stem from './components/blocks/Stem.vue';
  import About from './components/blocks/About.vue';
  import ReportPreview from './components/blocks/ReportPreview.vue';
  import BetterGreater from './components/blocks/BetterGreater.vue';
  import TrustPilots from './components/blocks/TrustPilots.vue';
  import Footer from './components/blocks/Footer.vue';

  import { ref, onMounted, onUnmounted } from 'vue';
  import FeaturedIn from './components/blocks/FeaturedIn.vue';
  const isMobile = ref(window.innerWidth < 1024);

  function handleResize() {
    isMobile.value = window.innerWidth < 1024;
  }

  onMounted(() => {
    window.addEventListener('resize', handleResize);
  });

  onUnmounted(() => {
    window.removeEventListener('resize', handleResize);
  });
</script>

<template>
  <Header />
  <FirstScreen />
  <Stem :isMobile=isMobile />
  <About />
  <ReportPreview :isMobile=isMobile />
  <BetterGreater />
  <TrustPilots :isMobile=isMobile />
  <FeaturedIn :isMobile=isMobile />
  <Footer :isMobile=isMobile />
</template>
