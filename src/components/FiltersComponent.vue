<template>
  <aside :class="`filters ${show ? 'filters--open' : ''}`">
    <img
      :src="image('cancel.svg')"
      alt="Fermer"
      class="icon icon--filters mobile"
      @click="close"
    />

    <div class="filters__content">
      <genders-component :genders="genders" @genders-selected="setGenders" />
      <prices-component :prices="prices" @prices-selected="setPrices" />
      <colors-component :colors="colors" @colors-selected="setColors" />
    </div>

    <div class="filters__buttons mobile">
      <button type="button" class="button button--outlined" @click="clear">
        {{
          getNumberOfFilters === 0
            ? 'Effacer'
            : `Effacer (${getNumberOfFilters})`
        }}
      </button>
      <button type="button" class="button button--filled" @click="close">
        Appliquer
      </button>
    </div>
  </aside>
</template>

<script>
import GendersComponent from './GendersComponent.vue';
import PricesComponent from './PricesComponent.vue';
import ColorsComponent from './ColorsComponent.vue';

export default {
  name: 'FiltersComponent',
  components: {
    GendersComponent,
    PricesComponent,
    ColorsComponent,
  },
  props: {
    show: Boolean,
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
  computed: {
    getNumberOfFilters() {
      return (
        this.selected.genders.length +
        this.selected.prices.length +
        this.selected.colors.length
      );
    },
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
    close() {
      this.$emit('close');
    },
    clear() {
      this.selected = {
        genders: [],
        prices: [],
        colors: [],
      };

      this.emit();
    },
    image(name) {
      return require(`@/assets/img/${name}`);
    },
  },
};
</script>

<style lang="scss" scoped></style>
