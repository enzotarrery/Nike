<template>
  <section class="filter colors">
    <header class="header header--hoverable" @click="toggle">
      <h2 class="title filter__title">
        Couleur {{ selected.length === 0 ? null : `(${selected.length})` }}
      </h2>
      <img
        :src="image('chevron.svg')"
        alt="Flèche"
        :class="`icon ${open ? '' : 'icon--rotate180'} desktop`"
      />
    </header>

    <div :class="`fields fields--colors ${open ? '' : 'fields--hidden'}`">
      <color-component
        v-for="(color, index) in colors"
        :key="index"
        :color="color"
        @color-add="addColor"
        @color-remove="removeColor"
      />
    </div>
  </section>
</template>

<script>
import ColorComponent from './ColorComponent.vue';

export default {
  name: 'ColorsComponent',
  components: { ColorComponent },
  props: {
    colors: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      open: true,
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
    toggle() {
      this.open = !this.open;
    },
    emit() {
      this.$emit('colors-selected', this.selected);
    },
    image(name) {
      return require(`@/assets/img/${name}`);
    },
  },
};
</script>

<style lang="scss" scoped></style>
