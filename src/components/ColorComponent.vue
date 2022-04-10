<template>
  <div>{{ color }}</div>
</template>

<script>
export default {
  name: 'ColorComponent',
  props: {
    color: String,
  },
};
</script>

<style lang="scss" scoped></style>
