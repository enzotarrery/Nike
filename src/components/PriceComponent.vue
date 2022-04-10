<template>
  <label :for="`price-${price}`">
    {{ price }}
    <input
      type="checkbox"
      :name="`price-${price}`"
      :id="`price-${price}`"
      @change="updatePrice"
    />
  </label>
</template>

<script>
export default {
  name: 'PriceComponent',
  props: {
    price: String,
  },
  methods: {
    updatePrice(event) {
      const checkbox = event.target;

      if (checkbox.checked) {
        this.$emit('price-add');
      } else {
        this.$emit('price-remove');
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
