<script lang="ts" setup="">
import { defineEmits, defineProps, withDefaults } from 'vue'

const props = defineProps({
  title: {
    type: String,
    default: 'placeholder',
  },
  img: {
    type: String,
    default: 'placeholder',
  },
})
</script>

<template>
  <div>
    <div class="bg-black h-40">
      <Icon :name="'projects/' + img" class="object-cover h-full w-full" />
    </div>
    <div class="bg-primary row-span-1 text-white">
      {{ title }}
    </div>
  </div>
  <!--  <div class="grid grid-rows-4">-->
  <!--    <div class="bg-black row-span-3">-->
  <!--      <Icon :name="'projects/' + img" />-->
  <!--    </div>-->
  <!--    <div class="bg-primary row-span-1 text-white">{{ title }}</div>-->
  <!--  </div>-->
</template>

<style lang="postcss" scoped></style>
