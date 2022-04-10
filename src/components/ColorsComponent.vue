<template>
  <section class="colors">
    <header class="header">
      <h2 class="title" v-if="checked === 0">Couleur</h2>
      <h2 class="title" v-else>Couleur ({{ checked }})</h2>
    </header>

    <color-component
      v-for="(color, index) in colors"
      :key="index"
      :color="color"
      @color-add="addColor"
      @color-remove="removeColor"
    />
  </section>
</template>

<script>
import ColorComponent from './ColorComponent.vue';

export default {
  name: 'ColorsComponent',
  components: { ColorComponent },
  props: {
    colors: Array,
  },
  data() {
    return {
      checked: 0,
    };
  },
  methods: {
    addColor() {
      this.checked++;
    },
    removeColor() {
      this.checked--;
    },
  },
};
</script>

<style lang="scss" scoped></style>
