<template>
  <div class="field gender">
    <input
      type="checkbox"
      :name="gender"
      :id="gender"
      class="field__checkbox"
      @change="updateGender"
    />
    <label :for="gender" class="field__label field__label--capitalized">
      {{ gender }}
    </label>
  </div>
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
