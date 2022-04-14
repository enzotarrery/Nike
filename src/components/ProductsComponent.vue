<template>
  <div class="products" v-if="filteredProducts.length !== 0">
    <product-component
      v-for="(product, index) in filteredProducts"
      :key="index"
      :product="product"
    />
  </div>

  <div class="products" v-else>
    <p class="products__message">Aucun produit correspondant aux critères.</p>
  </div>
</template>

<script>
import ProductComponent from './ProductComponent.vue';

export default {
  name: 'ProductsComponent',
  components: { ProductComponent },
  props: {
    filters: { type: Object, required: true },
  },
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
        this.products = response.filter(
          (product) => !this.emptyProduct(product)
        );

        /* Deduce the genders & colors */
        let genders = [];
        let colors = [];

        this.products.forEach((product) => {
          if (
            product.sexe !== '' &&
            !genders.includes(product.sexe.toLowerCase())
          ) {
            genders.push(product.sexe.toLowerCase());
          }

          product.couleur.split(', ').forEach((color) => {
            if (color !== '' && !colors.includes(color.toLowerCase())) {
              colors.push(color.toLowerCase());
            }
          });
        });

        /* The data is emitted to the parent in order to be rendered */
        this.$emit('genders-update', genders);
        this.$emit('colors-update', colors);
      })
      .catch((error) =>
        console.warn(`ERREUR [${error.code}] : ${error.message}.`)
      );
  },
  methods: {
    emptyProduct(product) {
      const values = Object.values(product).filter((value) => value !== '');

      return values.length <= 0;
    },
    getPriceAsFloat(string) {
      return parseFloat(string.slice(0, -2).replace(',', '.'));
    },
    checkGender(product) {
      return this.filters.genders.length !== 0
        ? this.filters.genders.includes(product.sexe.toLowerCase())
        : true;
    },
    checkPrices(product) {
      if (this.filters.prices.length === 0) {
        return true;
      }

      const productPrice = this.getPriceAsFloat(product.prix);

      for (let price of this.filters.prices) {
        if (
          price.min <= productPrice &&
          (price.max ? productPrice <= price.max : true)
        ) {
          return true;
        }
      }
    },
    checkColors(product) {
      return this.filters.colors.every((color) =>
        product.couleur.toLowerCase().split(', ').includes(color)
      );
    },
  },
  computed: {
    filteredProducts() {
      return this.products.filter(
        (product) =>
          this.checkGender(product) &&
          this.checkPrices(product) &&
          this.checkColors(product)
      );
    },
  },
};
</script>

<style lang="scss" scoped></style>
