<template>
  <section class="genders">
    <header class="header">
      <h2 class="title" v-if="selected.length === 0">Genre</h2>
      <h2 class="title" v-else>Genre ({{ selected.length }})</h2>
    </header>

    <gender-component
      v-for="(gender, index) in genders"
      :key="index"
      :gender="gender"
      @gender-add="addGender"
      @gender-remove="removeGender"
    />
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
  },
};
</script>

<style lang="scss" scoped></style>
