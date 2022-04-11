<template>
  <products-view />
</template>

<script>
import ProductsView from './views/ProductsView.vue';

export default {
  name: 'App',
  components: { ProductsView },
};
</script>

<style lang="scss">
@use '@/assets/scss/style.scss';
</style>
