<template>
  <img :src="image(name)" :alt="alt" class="icon" />
</template>

<script>
export default {
  name: 'IconComponent',
  props: {
    name: {
      type: String,
      required: true,
    },
    alt: {
      type: String,
      required: false,
    },
  },
  computed: {
    image(name) {
      return require(`@/assets/img/${name}`);
    },
  },
};
</script>

<style lang="scss" scoped></style>
