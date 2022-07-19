<template>
  <div class="articles-page">
    <h1 class="text-2xl font-bold">Список статей</h1>
    <ul>
      <li v-for="(article, index) in articles" :key="index">
        <nuxt-link :to="`${article.slug}/`">{{ article.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ArticlesPage',

  async asyncData({ $content }) {
    const articles = await $content('articles').fetch()
    return { articles }
  }
}
</script>

<style lang="scss">

</style>
