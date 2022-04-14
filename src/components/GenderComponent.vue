<template>
  <label :for="`${gender}`" class="filter__label filter__label--capitalized">
    <input
      type="checkbox"
      :name="`${gender}`"
      :id="`${gender}`"
      class="filter__checkbox"
      @change="updateGender"
    />
    {{ gender }}
  </label>
</template>

<script>
export default {
  name: 'GenderComponent',
  props: {
    gender: String,
  },
  methods: {
    updateGender(event) {
      const checkbox = event.target;

      if (checkbox.checked) {
        this.$emit('gender-add', this.gender);
      } else {
        this.$emit('gender-remove', this.gender);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
