<template>
  <article class="article">
    <nuxt-content :document="page" />
    <small>
      {{ page.author }}
    </small>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const page = await $content('articles', params.slug).fetch()

    return {
      page,
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
