<template>
  <section class="genders">
    <header class="header">
      <h2 class="title" v-if="checked === 0">Genre</h2>
      <h2 class="title" v-else>Genre ({{ checked }})</h2>
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
      checked: 0,
    };
  },
  methods: {
    addGender() {
      this.checked++;
    },
    removeGender() {
      this.checked--;
    },
  },
};
</script>

<style lang="scss" scoped></style>
