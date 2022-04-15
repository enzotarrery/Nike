<template>
  <section class="filter">
    <header class="header header--hoverable" @click="toggle">
      <h2 class="title filter__title">
        Rechercher par prix
        {{ selected.length === 0 ? null : `(${selected.length})` }}
      </h2>
      <img
        :src="image('chevron.svg')"
        alt="Flèche"
        :class="`icon ${open ? '' : 'icon--rotate180'} desktop`"
      />
    </header>

    <div :class="`fields ${open ? '' : 'fields--hidden'}`">
      <price-component
        v-for="(price, index) in prices"
        :key="index"
        :price="price"
        @price-add="addPrice"
        @price-remove="removePrice"
      />
    </div>
  </section>
</template>

<script>
import PriceComponent from './PriceComponent.vue';

export default {
  components: { PriceComponent },
  name: 'PricesComponent',
  props: {
    prices: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      open: true,
      selected: [],
    };
  },
  methods: {
    addPrice(price) {
      this.selected.push(price);

      this.emit();
    },
    removePrice(price) {
      this.selected = this.selected.filter(
        (selectedPrice) => selectedPrice !== price
      );

      this.emit();
    },
    emit() {
      this.$emit('prices-selected', this.selected);
    },
    toggle() {
      this.open = !this.open;
    },
    image(name) {
      return require(`@/assets/img/${name}`);
    },
  },
};
</script>

<style lang="scss" scoped></style>
