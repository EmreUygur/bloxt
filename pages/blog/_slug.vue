<template>
  <article class="article">
    <h1>{{ page.title }}</h1>
    <p class="description">{{ page.description }}</p>
    <nuxt-content :document="page" />
    <small>
      {{ page.author }}
    </small>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const result = await $content('articles')
      .where({ slug: params.slug })
      .limit(1)
      .fetch()

    return {
      page: result[0],
    }
  },
  head() {
    return {
      title: this.page.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.page.description,
        },
      ],
    }
  },
}
</script>

<style lang="scss">
.nuxt-content {
  img {
    width: 100%;
  }
}
</style>
