<template>
  <label :for="`price-${price}`">
    {{ price }} €
    <input type="checkbox" :name="`price-${price}`" :id="`price-${price}`" />
  </label>
</template>

<script>
export default {
  name: 'PriceComponent',
  props: {
    price: String,
  },
};
</script>
