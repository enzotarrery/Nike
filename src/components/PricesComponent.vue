<template>
  <section class="prices">
    <header class="header">
      <h2 class="title" v-if="checked === 0">Recherche par prix</h2>
      <h2 class="title" v-else>Recherche par prix ({{ checked }})</h2>
    </header>

    <price-component
      v-for="(price, index) in prices"
      :key="index"
      :price="price"
      @price-add="addPrice"
      @price-remove="removePrice"
    />
  </section>
</template>

<script>
import PriceComponent from './PriceComponent.vue';

export default {
  components: { PriceComponent },
  name: 'PricesComponent',
  props: {
    prices: Array,
  },
  data() {
    return {
      checked: 0,
    };
  },
  methods: {
    addPrice() {
      this.checked++;
    },
    removePrice() {
      this.checked--;
    },
  },
};
</script>

<style lang="scss" scoped></style>
