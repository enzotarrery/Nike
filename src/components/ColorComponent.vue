<template>
  <div class="color">
    <input
      type="checkbox"
      :name="color"
      :id="color"
      class="filter__checkbox color__checkbox"
      @change="updateColor"
    />
    <label
      :for="color"
      class="filter__label filter__label--capitalized color__label"
      :style="`background-color: ${getStyleColor(color)}`"
    >
      {{ color }}
    </label>
  </div>
</template>

<script>
export default {
  name: 'ColorComponent',
  props: {
    color: String,
  },
  methods: {
    getStyleColor(color) {
      switch (color) {
        case 'rouge':
          return 'red';
        case 'bleu':
          return 'blue';
        case 'jaune':
          return 'yellow';
        case 'rose':
          return 'pink';
        case 'noir':
          return 'black';
        case 'blanc':
          return 'white';
        case 'vert':
          return 'green';
        case 'gris':
          return 'grey';
        default:
          return null;
      }
    },
    updateColor(event) {
      const checkbox = event.target;

      if (checkbox.checked) {
        this.$emit('color-add', this.color);
      } else {
        this.$emit('color-remove', this.color);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
