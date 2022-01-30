<template>
  <img :src="iconUri" :class="[baseStyles]" />
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Icon",
  props: {
    name: {
      type: String,
      required: true,
    },
    inverted: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    iconUri(): string {
      return `/icons/${this.name}.svg`;
    },
    baseStyles(): { [key: string]: boolean } {
      return {
        inverted: this.inverted,
      };
    },
  },
});
</script>

<style scoped lang="postcss">
.inverted {
  filter: brightness(0) invert(1);
}
</style>
