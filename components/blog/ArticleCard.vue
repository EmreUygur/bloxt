<template>
  <nuxt-link :to="link" class="card">
    <div class="card-header">
      <div class="card-title">
        {{ title }}
      </div>
      <div class="card-createdAt">
        {{ date }}
      </div>
    </div>
    <div class="card-description">
      {{ description }}
    </div>
    <div class="card-author">
      {{ author }}
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    slug: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    author: {
      type: String,
      required: true,
    },
    createdAt: {
      type: String,
      required: true,
    },
  },
  computed: {
    link() {
      return `/blog/${this.slug}`
    },
    date() {
      const date = new Date(this.createdAt)

      const day = date.getDay() + 1
      const month = date.getMonth() + 1
      const year = date.getFullYear()
      return `${day}.${month}.${year}`
    },
  },
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/palette.scss';

.card {
  padding: 2.5rem;
  display: flex;
  flex-direction: column;
  background-color: $cardBackground;
  border-radius: 3px;
  outline: none;
  color: $headline;
  text-decoration: none;
  cursor: pointer;

  &-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
  }
  &-title {
    font-size: 2rem;
    font-weight: 600;
  }
  &-createdAt {
    font-size: 1.2rem;
  }
  &-description {
    color: $paragraph;
    font-size: 1.1rem;
  }
}
</style>
