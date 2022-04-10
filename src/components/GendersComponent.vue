<template>
  <div class="genders">
    <gender-component
      v-for="(gender, index) in genders"
      :key="index"
      :gender="gender"
    />
  </div>
</template>

<script>
import GenderComponent from './GenderComponent.vue';

export default {
  components: { GenderComponent },
  name: 'GendersComponent',
  props: {
    genders: Array,
  },
};
</script>

<style lang="scss" scoped></style>
