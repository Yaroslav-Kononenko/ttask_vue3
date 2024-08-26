<script setup lang="ts">
  interface Card {
    image: string;
  }

  defineProps<{ cards: Card[] }>();
</script>

<template>
  <div class="grid">
    <div
      v-for="(card, index) in cards"
      :key="index"
      class="grid__item"
    >
      <div class="card">
        <img :src="card.image" :alt="`Card ${index + 1}`" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .grid {
    row-gap: 24px;
  }

  .grid__item {
    grid-column: span 4;
  }
  
  .card {  
    img {
      width: 100%;
      border-radius: 8px;
    }
  }
</style>
