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
@import '~/assets/styles/palette.scss';

.link {
  outline: none;
  &.default {
    color: $link;
  }
  &.navbar-brand {
    text-decoration: none;
    font-size: 36px;
    font-weight: 600;
    color: $buttonText;
  }
  &.navbar-link {
    text-decoration: none;
    font-size: 18px;
    font-weight: 600;
    letter-spacing: -0.03rem;
    color: $buttonText;
  }
}
</style>
