<template>
  <label :for="`color-${color}`">
    {{ color }}
    <input
      type="checkbox"
      :name="`color-${color}`"
      :id="`color-${color}`"
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
        this.$emit('color-add');
      } else {
        this.$emit('color-remove');
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
