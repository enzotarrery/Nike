<template>
  <aside class="filters">
    <genders-component :genders="genders" @genders-selected="setGenders" />
    <prices-component :prices="prices" @prices-selected="setPrices" />
    <colors-component :colors="colors" @colors-selected="setColors" />
  </aside>
</template>

<script>
import GendersComponent from './GendersComponent.vue';
import PricesComponent from './PricesComponent.vue';
import ColorsComponent from './ColorsComponent.vue';

export default {
  name: 'FiltersComponent',
  components: { GendersComponent, PricesComponent, ColorsComponent },
  props: {
    genders: Array,
    prices: Array,
    colors: Array,
  },
  data() {
    return {
      selected: {
        genders: [],
        prices: [],
        colors: [],
      },
    };
  },
  methods: {
    setGenders(genders) {
      this.selected.genders = genders;

      this.emit();
    },
    setPrices(prices) {
      this.selected.prices = prices;

      this.emit();
    },
    setColors(colors) {
      this.selected.colors = colors;

      this.emit();
    },
    emit() {
      this.$emit('filter', this.selected);
    },
  },
};
</script>

<style lang="scss" scoped></style>
