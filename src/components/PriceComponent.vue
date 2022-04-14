<template>
  <label :for="`${price.min}-${price.max}`" class="filter__label">
    <input
      type="checkbox"
      :name="`${price.min}-${price.max}`"
      :id="`${price.min}-${price.max}`"
      class="filter__checkbox"
      @change="updatePrice"
    />
    {{
      price.min === 0
        ? `Moins de ${price.max}€`
        : !price.max
        ? `Plus de ${price.min}€`
        : `${price.min}€ - ${price.max}€`
    }}
  </label>
</template>

<script>
export default {
  name: 'PriceComponent',
  props: {
    price: Object,
  },
  methods: {
    updatePrice(event) {
      const checkbox = event.target;

      if (checkbox.checked) {
        this.$emit('price-add', this.price);
      } else {
        this.$emit('price-remove', this.price);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
