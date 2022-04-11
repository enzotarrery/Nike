<template>
  <section class="prices">
    <header class="header">
      <h2 class="title" v-if="selected.length === 0">Recherche par prix</h2>
      <h2 class="title" v-else>Recherche par prix ({{ selected.length }})</h2>
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
      selected: [],
    };
  },
  methods: {
    addPrice(price) {
      this.selected.push(price);

      this.emit();
    },
    removePrice(price) {
      this.selected = this.selected.filter(
        (selectedPrice) => selectedPrice !== price
      );

      this.emit();
    },
    emit() {
      this.$emit('prices-selected', this.selected);
    },
  },
};
</script>

<style lang="scss" scoped></style>
