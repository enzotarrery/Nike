<template>
  <div class="prices">
    <price-component
      v-for="(price, index) in prices"
      :key="index"
      :price="price"
    />
  </div>
</template>

<script>
import PriceComponent from './PriceComponent.vue';

export default {
  components: { PriceComponent },
  name: 'PricesComponent',
  props: {
    prices: Array,
  },
};
</script>

<style lang="scss" scoped></style>
