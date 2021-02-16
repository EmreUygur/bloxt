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
      default: 'default',
      validator(variant) {
        return ['navbar-brand', 'navbar-link', 'default'].includes(variant)
      },
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
  &.navbar-brand {
    font-size: 36px;
    font-weight: 600;
  }
  &.navbar-link {
    font-size: 24px;
  }
}
</style>
