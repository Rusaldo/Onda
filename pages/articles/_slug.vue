<template>
  <section class="article-page bg-white dark:bg-gray-900">
    <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16 lg:px-6">
      <div class="max-w-screen-lg text-gray-500 sm:text-lg dark:text-gray-400">
        <h2 class="mb-4 text-4xl tracking-tight font-bold text-gray-900 dark:text-white">
          {{ article.title }}
        </h2>
        <nuxt-content class="font-light"
                      :document="article" />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ArticlePage',

  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()
    return {
      article
    }
  },

  head() {
    return {
      title: this.article.title,
      meta: [
        { hid: 'description', name: 'description', content: this.article.description },
        { hid: 'og:title', property: 'og:title', content: this.article.title },
        { hid: 'og:description', property: 'og:description', content: this.article.description },
      ]
    }
  }
}
</script>

<style lang="scss">

</style>
