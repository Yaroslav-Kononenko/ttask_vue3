<script setup lang="ts">
  import ActionButtonComponent from './../atoms/ActionButtonComponent.vue';

  type listData = {
    icon: String;
    text: String;
  };

  const listData: listData[] = [{
    icon: '👩‍🏫',
    text: 'A 1-on-1 live lesson with math teacher'
  },{
    icon: '📊',
    text: 'Your kid math level analysis with strong and weak sides outline'
  },{
    icon: '📄',
    text: 'Learning plan to improve in math',
  }];
</script>

<template>
  <section class="first-screen grid">
    <div class="grid__item grid__item--desktop-1-6 info-box">
      <div class="text-container">
        <h1>
          Check your child’s
          <br>
          math level
        </h1>
      </div>

      <div class="text-container">
        <div class="grades">
          <span>
            Grades&nbsp;1-8
          </span>
        </div>
      </div>

      <div class="info-box__main">
        <div class="accent title">
            Take a knowledge evaluation test
            to determine your child's math level and 
            <span class="accent--green">receive a learning plan</span> 
            to thrive in math
        </div>

        <ul class="text-list">
          <li
            class="test-list__row" 
            v-for="(listItem, index) in listData" :key="index"
          >
            <span class="list-icon">{{ listItem.icon }}</span>
            <span>{{ listItem.text }}</span>
          </li>
        </ul>
      </div>

      <div class="button-container">
        <ActionButtonComponent />
      </div>
    </div>

    <div class="image-box grid__item grid__item--desktop-8-12">
      <img class="main-img image-box__item" src="../../assets/boy.webp" alt="Student-Boy">
    </div>
  </section>
</template>

<style lang="scss">
  .first-screen {
    margin-bottom: 40px;
    padding-left: 8px;
    padding-right: 8px;

    @include ondesktop {
      margin-bottom: 0;
    }
  }

  .button-container {
    margin: 0 auto;

    @include ondesktop {
      margin: 0;
    }
  }

  .info-box {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    margin-bottom: 16px;

    &__main {
      margin-bottom: 16px;
    }

    @include ondesktop {
      justify-content: center;
      align-items: start;
      margin-bottom: 0;
      gap: 16;

      &__main {
        margin-bottom: 24px;
      }
    }
  }

  .grades {
    display: inline-block;
    padding: 4px 8px;
    background-color: #d0dbf1;
    border-radius: 4px;

    font-size: 14px;
    line-height: 24px;
    font-weight: 800;

    @include ondesktop {
      display: none;
    }
  }

  .text-list {
    display: flex;
    flex-direction: column;
    gap: 12px;
    list-style: none;
    padding: 0;
    margin: 0;

    &__row {
      display: flex;
      align-items: baseline;
    }
  }

  .list-icon {
    width: 16px;
    height: 16px;
    margin-right: 8px;
  }

  .main-img {
    width: 100%;
    object-fit: contain;
  }

  .text-container {
    text-align: center;

    @include ondesktop {
      text-align: left;
    }
  }

  .image-box {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: 20px;
    background-color: #ffffff;

    &__item {
      grid-column: 2/4;
    }

    @include ondesktop {
      display: block;
      background-color: $mainBgColor;
    }
  }
</style>
