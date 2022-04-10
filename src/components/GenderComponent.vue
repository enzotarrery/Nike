<template>
  <label :for="`gender-${gender}`">
    {{ gender }}
    <input
      type="checkbox"
      :name="`gender-${gender}`"
      :id="`gender-${gender}`"
    />
  </label>
</template>

<script>
export default {
  name: 'GenderComponent',
  props: {
    gender: String,
  },
};
</script>

<style lang="scss" scoped></style>
