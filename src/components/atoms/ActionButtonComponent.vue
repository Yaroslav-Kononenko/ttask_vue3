<script setup lang="ts">

defineProps<{ isAccent?: boolean }>()

</script>

<template>
  <button class="linkButton" :class="{ 'accent': isAccent }">Get&nbsp;a&nbsp;lesson</button>
</template>

<style scoped lang='scss'>
  .linkButton {
    display: inline-block;
    padding: 16px 32px;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    line-height: 24px;
    font-weight: 800;
    color: $buttonTextColor;
    background-color: $buttonBgColorEnabled;
    cursor: pointer;

    &:hover {
      background-color: $buttonBgColorHovered;
    }

    &:active {
      background-color: $buttonBgColorPressed;
    }
  }

  .accent {
    background-color: $colorAccent-green;
  }
</style>