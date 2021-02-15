<template>
  <nuxt-link class="link" :class="variant" :to="to">
    {{ label }}
  </nuxt-link>
</template>

<script>
export default {
  props: {
    to: {
      type: String,
      required: true,
    },
    variant: {
      type: String,
      required: false,
      default: '',
    },
    label: {
      type: String,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.link {
  color: #000;
  text-decoration: none;
  outline: none;
}
</style>
