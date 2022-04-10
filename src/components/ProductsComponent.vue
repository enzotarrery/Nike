<template>
  <div class="products">
    <product-component
      v-if="searchedProducts.length !== 0"
      v-for="(product, index) in searchedProducts"
      :key="index"
      :product="product"
    />

    <p v-else>Aucun produit correspondant aux critères.</p>
  </div>
</template>

<script>
import ProductComponent from './ProductComponent.vue';

export default {
  name: 'ProductsComponent',
  components: { ProductComponent },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    fetch('/assets/db/produits.json')
      .then((response) => response.json())
      .then((response) => {
        this.products = response;
      })
      .catch((error) =>
        console.log(`ERREUR [${error.code}] : ${error.message}.`)
      );
  },
};
</script>

<style lang="scss" scoped></style>
