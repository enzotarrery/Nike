<template>
  <section class="filter">
    <header class="header" @click="toggle">
      <h2 class="title filter__title">
        Genre {{ selected.length === 0 ? null : `(${selected.length})` }}
      </h2>
      <img
        :src="image('chevron.svg')"
        alt="Flèche"
        :class="`icon ${open ? '' : 'icon--rotate180'} desktop`"
      />
    </header>

    <div :class="`fields ${open ? '' : 'fields--hidden'}`">
      <gender-component
        v-for="(gender, index) in genders"
        :key="index"
        :gender="gender"
        @gender-add="addGender"
        @gender-remove="removeGender"
      />
    </div>
  </section>
</template>

<script>
import GenderComponent from './GenderComponent.vue';

export default {
  name: 'GendersComponent',
  components: { GenderComponent },
  props: {
    genders: Array,
  },
  data() {
    return {
      open: true,
      selected: [],
    };
  },
  methods: {
    addGender(gender) {
      this.selected.push(gender);

      this.emit();
    },
    removeGender(gender) {
      this.selected = this.selected.filter(
        (selectedGender) => selectedGender !== gender
      );

      this.emit();
    },
    emit() {
      this.$emit('genders-selected', this.selected);
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
