<template>
  <label :for="`${gender}`" class="gender__label">
    {{ gender }}
    <input
      type="checkbox"
      :name="`${gender}`"
      :id="`${gender}`"
      class="gender__checkbox"
      @change="updateGender"
    />
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
