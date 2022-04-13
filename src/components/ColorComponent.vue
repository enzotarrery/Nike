<template>
  <label :for="`${color}`" class="color__label">
    {{ color }}
    <input
      type="checkbox"
      :name="`${color}`"
      :id="`${color}`"
      class="color__checkbox"
      @change="updateColor"
    />
  </label>
</template>

<script>
export default {
  name: 'ColorComponent',
  props: {
    color: String,
  },
  methods: {
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
