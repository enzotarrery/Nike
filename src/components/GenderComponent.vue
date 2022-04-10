<template>
  <label :for="`gender-${gender}`">
    {{ gender }}
    <input
      type="checkbox"
      :name="`gender-${gender}`"
      :id="`gender-${gender}`"
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
        this.$emit('gender-add');
      } else {
        this.$emit('gender-remove');
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
