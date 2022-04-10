<template>
  <div class="colors">
    <color-component
      v-for="(color, index) in colors"
      :key="index"
      :color="color"
    />
  </div>
</template>

<script>
import ColorComponent from './ColorComponent.vue';

export default {
  name: 'ColorsComponent',
  components: { ColorComponent },
  props: {
    colors: Array,
  },
};
</script>

<style lang="scss" scoped></style>
