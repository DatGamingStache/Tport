<script lang="ts" setup="">
import { defineEmits, defineProps, withDefaults } from 'vue'
const props = defineProps({
  techStackName: {
    type: String,
    default: 'default',
  },

})
const techStackMap = {
  pdanalytics: [{ name: 'Vue3' }, { name: 'MongoDb' }, { name: 'TypeScript' }, { name: 'Jest', description: 'Unit Testing' }, { name: 'MVVM', description: 'Architecture' }],
  adstakr: [{ name: 'Vue3' }, { name: 'TypeScript' }, { name: 'Jest', description: 'Unit Testing' }, { name: 'MVC', description: 'Architecture' }],
  big3d: [{ name: 'Vue3' }, { name: 'TypeScript' }, { name: 'MVC', description: 'Architecture' }],
  boostehr: [{ name: 'React Native' }, { name: 'MVC', description: 'Architecture' }],
  tboi: [{ name: 'Vue3' }, { name: 'TypeScript' }, { name: 'Jest', description: 'Unit Testing' }, { name: 'MVC', description: 'Architecture' }],
  kickthekeeper: [{ name: 'Vue3' }, { name: 'TypeScript' }, { name: 'Jest', description: 'Unit Testing' }, { name: 'MVC', description: 'Architecture' }],
  crisiscleanup: [{ name: 'Vue2' }, { name: 'MongoDb' }, { name: 'TypeScript' }, { name: 'Jest', description: 'Unit Testing' }, { name: 'MVVM', description: 'Architecture' }],
}
</script>

<template>
  <div v-for="(item,idx) in techStackMap[techStackName]" :key="idx" class="flex gap-2  items-center">
    <Icon :name="'TechStack/' + item.name" class="w-10 h-10" />
    <Text>{{ item.name }}</Text>
    <div v-if="item.description">
      - <Text>{{ item.description }}</Text>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
</style>
