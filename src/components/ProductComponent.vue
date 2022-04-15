<template>
  <figure class="product">
    <img class="product__thumbnail" :src="image" :alt="product.article" />

    <figcaption class="product__content">
      <h3 class="product__title">{{ product.article }}</h3>
      <p class="product__detail">
        Chaussure {{ product.sexe === 'Mixte' ? '' : `pour ${product.sexe}` }}
      </p>
      <p class="product__detail">
        {{
          product.couleur.split(', ').length === 1
            ? `${product.couleur.split(', ').length} couleur`
            : `${product.couleur.split(', ').length} couleurs`
        }}
      </p>
      <p class="product__price">{{ product.prix }}</p>
    </figcaption>
  </figure>
</template>

<script>
export default {
  name: 'ProductComponent',
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  computed: {
    image() {
      return this.product.photo
        ? require(`@/assets/img/${this.product.photo}`)
        : null;
    },
  },
};
</script>

<style lang="scss" scoped></style>
