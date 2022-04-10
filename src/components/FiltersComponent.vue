<template>
  <aside class="filters">
    <genders-component :genders="genders" />
    <prices-component :prices="prices" />
    <colors-component :colors="colors" />
  </aside>
</template>

<script>
import GendersComponent from './GendersComponent.vue';
import PricesComponent from './PricesComponent.vue';
import ColorsComponent from './ColorsComponent.vue';

export default {
  name: 'FiltersComponent',
  components: { GendersComponent, ColorsComponent, PricesComponent },
  props: {
    genders: Array,
    prices: Array,
    colors: Array,
  },
};
</script>

<style lang="scss" scoped></style>
