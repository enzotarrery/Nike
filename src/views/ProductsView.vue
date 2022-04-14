<template>
  <main>
    <section class="products-page">
      <header class="header header--main">
        <h2 class="title">
          Nouveautés
          {{ title }}
        </h2>
        <img
          :src="image('adjustments.svg')"
          alt="Filtrer"
          class="icon mobile"
          @click="open"
        />
      </header>

      <filters-component
        :genders="genders"
        :prices="prices"
        :colors="colors"
        :show="show"
        @filter="setSelected"
        @close="close"
      />

      <products-component
        :filters="selected"
        @genders-update="setGenders"
        @colors-update="setColors"
      />
    </section>
  </main>
</template>

<script>
import FiltersComponent from '@/components/FiltersComponent.vue';
import ProductsComponent from '@/components/ProductsComponent.vue';

export default {
  name: 'ProductsView',
  components: { FiltersComponent, ProductsComponent },
  data() {
    return {
      title: '',
      genders: [],
      prices: [
        {
          min: 0,
          max: 50,
        },
        {
          min: 50,
          max: 100,
        },
        {
          min: 100,
          max: 150,
        },
        {
          min: 150,
          max: null,
        },
      ],
      colors: [],
      selected: {
        genders: [],
        prices: [],
        colors: [],
      },
      show: false,
    };
  },
  methods: {
    setGenders(genders) {
      this.genders = genders;
    },
    setPrices(prices) {
      this.prices = prices;
    },
    setColors(colors) {
      this.colors = colors;
    },
    setSelected(selected) {
      this.selected = selected;

      this.setTitle();
    },
    setTitle() {
      let title = [];

      for (let key in this.selected) {
        /* Management of the prices */
        if (key === 'prices') {
          let prices = [];

          for (let price of this.selected[key]) {
            prices.push(
              price.min === 0
                ? `Moins de ${price.max}€`
                : !price.max
                ? `Plus de ${price.min}€`
                : `${price.min}€ - ${price.max}€`
            );
          }

          title = title.concat(prices);
        } else {
          /* Anything else */
          title = title.concat(this.selected[key]);
        }
      }

      this.title = title.join(' ');
    },
    open() {
      this.show = true;
    },
    close() {
      this.show = false;
    },
    image(name) {
      return require(`@/assets/img/${name}`);
    },
  },
};
</script>

<style lang="scss" scoped></style>
