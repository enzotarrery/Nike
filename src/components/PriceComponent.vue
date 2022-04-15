<template>
  <div class="field price">
    <input
      type="checkbox"
      :name="`${price.min}-${price.max}`"
      :id="`${price.min}-${price.max}`"
      class="field__checkbox"
      @change="updatePrice"
    />
    <label :for="`${price.min}-${price.max}`" class="field__label">
      {{
        price.min === 0
          ? `Moins de ${price.max}€`
          : !price.max
          ? `Plus de ${price.min}€`
          : `${price.min}€ - ${price.max}€`
      }}
    </label>
  </div>
</template>

<script>
export default {
  name: 'PriceComponent',
  props: {
    price: {
      type: Object,
      required: true,
    },
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
