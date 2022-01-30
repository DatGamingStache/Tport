<template>
  <div class="grid grid-cols-4 grid-rows-6 bg-primary h-full">
    <Icon name="TristonPhoto" class="h-full col-span-2" />
    <div class="text-white flex flex-col col-span-2 justify-center">
      <div class="text-2xl">
        Triston Lewis
      </div>
      <div>Web & Software Developer</div>
    </div>
    <div
      class="
        text-white
        row-end-7
        col-span-4
        flex
        items-center
        flex-col
        justify-center
      "
    >
      <div class="text-2xl">
        Contact Information
      </div>
      <div>Tony.lewis0398@gmail.com</div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import _ from 'lodash'
import { useRoute } from 'vue-router'

export default defineComponent({
  name: 'NavBar',
  setup() {
    const route = useRoute()
    const routes = ref<
    { key: string; aliases?: string[]; title?: string; iconName?: string }[]
    >([])

    const routeTitle = (s: string): string => _.startCase(s)
    const routeName = (s: string): string => _.replace(_.startCase(s), ' ', '')
    const activeClass = (key: string): string[] => {
      const activeRoute = route
      const navItemRoute = routes.value.find(r => r.key === key) || {
        aliases: [],
      }
      const isActive = activeRoute.matched.find(
        r =>
          r.name === routeName(key)
              || (navItemRoute.aliases || []).includes(r.name as string),
      )
      return isActive ? ['active'] : []
    }

    return {
      routes,
      routeTitle,
      routeName,
      activeClass,
    }
  },
})
</script>

<style scoped lang="postcss"></style>
