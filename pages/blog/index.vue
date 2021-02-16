<template>
  <div>
    <div class="articles">
      <ArticleCard
        v-for="article in articles"
        :key="article.title"
        :title="article.title"
        :author="article.author"
        :slug="article.slug"
        :description="article.description"
        :created-at="article.createdAt"
      />
    </div>
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

<style lang="scss" scoped>
.articles {
  width: 100%;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: auto;
}
</style>
