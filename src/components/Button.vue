<script lang="ts" setup="">
import { defineEmits, defineProps, withDefaults } from 'vue'
const props = defineProps({
  style: {
    type: String,
    default: 'default',
  },
  label: {
    type: String,
    default: 'default',
  },

})
</script>

<template>
  <input type="button" :class="style" :value="label">
</template>

<style lang="postcss" scoped>
.default {
  @apply p-2 bg-primary text-white w-1/6 rounded-xl;
}
.outline {
  @apply p-2 bg-white text-black w-1/6 rounded-xl;
}
</style>
