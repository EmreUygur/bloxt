<template>
  <div>
    <ul>
      <li v-for="article in articles" :key="article.title">
        <Link :to="`/blog/${article.slug}`" :label="article.title" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('articles')
      .only(['title', 'author', 'slug', 'description', 'createdAt'])
      .fetch()

    return {
      articles,
    }
  },
  head() {
    return {
      title: 'Blog',
    }
  },
}
</script>
