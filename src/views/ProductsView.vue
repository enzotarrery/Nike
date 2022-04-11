<template>
  <section class="products-page">
    <header class="header">
      <h2 class="title">Nouveautés</h2>
    </header>

    <filters-component :genders="genders" :prices="prices" :colors="colors" />

    <products-component
      @genders-update="setGenders"
      @colors-update="setColors"
    />
  </section>
</template>

<script>
import FiltersComponent from '@/components/FiltersComponent.vue';
import ProductsComponent from '@/components/ProductsComponent.vue';

export default {
  name: 'ProductsView',
  components: { FiltersComponent, ProductsComponent },
  data() {
    return {
      genders: [],
      prices: ['Moins de 50€', '50€ - 100€', '100€ - 150€', 'Plus de 150€'],
      colors: [],
    };
  },
  methods: {
    setGenders(genders) {
      this.genders = genders;
    },
    setPrices(prices) {
      this.prices = prices;
    },
    setColors(colors) {
      this.colors = colors;
    },
  },
};
</script>

<style lang="scss" scoped></style>
