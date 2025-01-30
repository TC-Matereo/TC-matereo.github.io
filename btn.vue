<template>
  <button @click="handleClick" :class="btnClass">
    {{ label }}
  </button>
</template>

<script setup>
import { defineProps, defineEmits, computed } from 'vue';

const props = defineProps({
  label: {
    type: String,
    default: 'Click me'
  },
  type: {
    type: String,
    default: 'primary' // primary, secondary, danger
  }
});

const emit = defineEmits(['click']);

const handleClick = () => {
  emit('click');
};

const btnClass = computed(() => {
  return {
    'bg-blue-500 hover:bg-blue-600 text-white': props.type === 'primary',
    'bg-gray-500 hover:bg-gray-600 text-white': props.type === 'secondary',
    'bg-red-500 hover:bg-red-600 text-white': props.type === 'danger',
    'px-4 py-2 rounded-lg transition-all duration-300'
  };
});
</script>

<style scoped>
button {
  font-size: 16px;
  font-weight: bold;
}
</style>