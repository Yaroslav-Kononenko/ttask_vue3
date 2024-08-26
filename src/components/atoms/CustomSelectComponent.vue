<script setup lang="ts">
  import { ref, watch, onMounted, defineProps } from 'vue';

  const props = defineProps({
    options: {
      type: Array as () => { value: string, label: string }[],
      required: true,
    },
    modelValue: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Select an option',
    }
  });

  const placeholder = ref('');

  onMounted(() => {
    if (props.options.length > 0) {
      selectedOption.value = props.options[0];
      placeholder.value = props.options[0].label;
    }
  });

  const emit = defineEmits(['update:modelValue']);

  const isOpen = ref(false);
  const selectedOption = ref(
    props.options.find(option => option.value === props.modelValue) || null
  );

  watch(() => props.modelValue, (newValue) => {
    selectedOption.value = props.options.find(option => option.value === newValue) || null;
  });

  function toggleDropdown() {
    isOpen.value = !isOpen.value;
  }

  function selectOption(option: { value: string, label: string }) {
    selectedOption.value = option;
    emit('update:modelValue', option.value);
    isOpen.value = false;
    toggleDropdown();
  }
</script>

<template>
  <div class="custom-select" @click="toggleDropdown">
    <div class="custom-select__selected">
      {{ selectedOption ? selectedOption.label : placeholder }}
    </div>

    <ul v-if="isOpen" class="custom-select__dropdown">
      <li
        v-for="option in options"
        :key="option.value"
        @click="selectOption(option)"
        class="custom-select__option"
      >
        {{ option.label }}
      </li>
    </ul>

    <div class="custom-select__arrow" >
      <img class="select-arrow" :class="{ 'open': isOpen }" src="../../assets/arrow-down.svg" alt="select arrow">
    </div>
  </div>
</template>

<style scoped lang="scss">
  .custom-select {
    display: flex;
    justify-content: space-between;
    position: relative;
    cursor: pointer;

    &__selected {
      font-size: 16px;
      line-height: 24px;
      font-weight: 500;
    }

    &__arrow {
      height: 24px;
    }

    &__dropdown {
      position: absolute;
      top: 100%;
      left: -16px;
      width: calc(100% + 32px);
      padding-left: 0;
      max-height: 150px;
      overflow-y: auto;
      border: 1px solid #D0DBF1;
      border-radius: 8px;
      background-color: #fff;
      z-index: 10;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }

    &__option {
      padding: 12px 16px;
      cursor: pointer;
      list-style: none;

      &:hover {
        background-color: #f5f5f5;
      }
    }

    .select-arrow {
      width: 24px;
      height: 24px;

      transition: transform 0.3s ease;

      &.open {
        transform: rotate(180deg);
      }
    }
  }
</style>
