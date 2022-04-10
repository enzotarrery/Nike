<template>
  <figure class="product">
    <img
      class="product__thumbnail"
      :src="product.photo"
      :alt="product.article"
    />

    <figcaption class="product__content">
      <h3 class="product__title">{{ product.article }}</h3>
      <p class="product__price">{{ product.prix }}</p>
    </figcaption>
  </figure>
</template>

<script>
export default {
  name: 'ProductComponent',
  props: {
    product: Object,
  },
};
</script>

<style lang="scss" scoped></style>
