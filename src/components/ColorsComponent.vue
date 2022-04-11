<template>
  <section class="colors">
    <header class="header">
      <h2 class="title" v-if="selected.length === 0">Couleur</h2>
      <h2 class="title" v-else>Couleur ({{ selected.length }})</h2>
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
      selected: [],
    };
  },
  methods: {
    addColor(color) {
      this.selected.push(color);

      this.emit();
    },
    removeColor(color) {
      this.selected = this.selected.filter(
        (selectedColor) => selectedColor !== color
      );

      this.emit();
    },
    emit() {
      this.$emit('colors-selected', this.selected);
    },
  },
};
</script>

<style lang="scss" scoped></style>
