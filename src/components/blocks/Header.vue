<template>
  <header class="header">
    <a href="https://brighterly.com/" target="_blank">
      <img src="../../assets/logo.svg" class="logo" alt="Brighterly logo" />
    </a>
  </header>
</template>

<style lang="scss">
  .header {
    display: flex;
    justify-content: center;
    margin-bottom: $headerTopPadding-mobile;
    padding-top: 8px;

    @include ondesktop {
      display: block;
      margin-bottom: $headerTopPadding-desktop;
      padding-top: 32px;
    }
  }

  .logo {
    width: 96px;
    height: 32px;

    @include ondesktop {
      width: 112px;
      height: 40px;
    }
  }
</style>
