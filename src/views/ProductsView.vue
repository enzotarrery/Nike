<template>
  <div class="products-page">
    <filters-component />

    <products-component />
  </div>
</template>

<script>
import FiltersComponent from '@/components/FiltersComponent.vue';
import ProductsComponent from '@/components/ProductsComponent.vue';

export default {
  name: 'ProductsView',
  components: { FiltersComponent, ProductsComponent },
  data() {
    return {
      gender: [],
      price: [],
      colors: [],
      colorChoices: [],
    };
  },
  computed: {
    searchedProducts() {
      return this.products.filter((product) => {});
    },
  },
};
</script>

<style lang="scss" scoped>
.products-page {
}
</style>
