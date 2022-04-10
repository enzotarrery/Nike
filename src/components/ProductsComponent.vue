<template>
  <div class="products__content" v-if="products.length !== 0">
    <product-component
      v-for="(product, index) in products"
      :key="index"
      :product="product"
    />
  </div>

  <div class="products__content" v-else>
    <p>Aucun produit correspondant aux critères.</p>
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
    fetch('/produits.json')
      .then((response) => response.json())
      .then((response) => {
        /* The data to be rendered */
        this.products = response;

        /* Deduce the genders & colors */
        let genders = [];
        let colors = [];

        this.products.forEach((product) => {
          if (product.sexe !== '' && !genders.includes(product.sexe)) {
            genders.push(product.sexe);
          }

          product.couleur.split(', ').forEach((color) => {
            if (color !== '' && !colors.includes(color)) {
              colors.push(color);
            }
          });
        });

        /* The data is emitted to the parent in order to be rendered */
        this.$emit('genders-update', genders);
        this.$emit('colors-update', colors);
      })
      .catch((error) =>
        console.log(`ERREUR [${error.code}] : ${error.message}.`)
      );
  },
};
</script>

<style lang="scss" scoped></style>
