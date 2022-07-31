<template>
  <div class="articles-page">
    <section class="bg-white dark:bg-gray-900">
      <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16 lg:px-6">
        <div class="mx-auto max-w-screen-sm text-center lg:mb-16 mb-8">
          <h2 class="mb-4 text-3xl lg:text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Все статьи</h2>
          <p class="font-light text-gray-500 sm:text-xl dark:text-gray-400">We use an agile approach to test assumptions and connect with the needs of your audience early and often.</p>
        </div>
        <div class="grid gap-8 lg:grid-cols-2">
          <article v-for="(article, index) in articles"
                   :key="index"
                   class="p-6 bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
            <div class="flex justify-between items-center mb-5 text-gray-500">
                  <span class="bg-primary-100 text-primary-800 text-xs font-medium inline-flex items-center px-2.5 py-0.5 rounded dark:bg-primary-200 dark:text-primary-800">
                      <svg class="mr-1 w-3 h-3" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M2 5a2 2 0 012-2h8a2 2 0 012 2v10a2 2 0 002 2H4a2 2 0 01-2-2V5zm3 1h6v4H5V6zm6 6H5v2h6v-2z" clip-rule="evenodd"></path><path d="M15 7h1a2 2 0 012 2v5.5a1.5 1.5 0 01-3 0V7z"></path></svg>
                      Статья
                  </span>
              <span class="text-sm">{{ article.createdAt }}</span>
            </div>
            <h2 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
              <nuxt-link :to="`${article.slug}/`">{{ article.title }}</nuxt-link>
            </h2>
            <p class="mb-5 font-light text-gray-500 dark:text-gray-400">{{ article.description }}</p>
            <div class="flex justify-between items-center">
              <nuxt-link :to="`${article.slug}/`" class="inline-flex items-center font-medium text-blue-600 dark:text-primary-500 hover:underline">
                Читать
                <svg class="ml-2 w-4 h-4" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
              </nuxt-link>
            </div>
          </article>
        </div>
      </div>
    </section>
<!--    <section class="text-gray-600 body-font overflow-hidden">-->
<!--      <div class="container px-5 py-24 mx-auto">-->
<!--        <div class="-my-8 divide-y-2 divide-gray-100">-->
<!--          <div v-for="(article, index) in articles"-->
<!--               :key="index"-->
<!--               class="max-w-2xl px-8 py-4 mx-auto bg-white rounded-lg shadow-md dark:bg-gray-800">-->
<!--            <div class="text-sm font-light text-gray-600 dark:text-gray-400">-->
<!--              {{ article.createdAt }}-->
<!--            </div>-->

<!--            <div class="mt-2">-->
<!--              <nuxt-link :to="`${article.slug}/`"-->
<!--                         class="text-2xl font-bold text-gray-700 dark:text-white hover:text-gray-600 dark:hover:text-gray-200 hover:underline">-->
<!--                {{ article.title }}-->
<!--              </nuxt-link>-->
<!--              <p class="mt-2 text-gray-600 dark:text-gray-300">-->
<!--                {{ article.description }}-->
<!--              </p>-->
<!--            </div>-->

<!--            <div class="mt-4">-->
<!--              <nuxt-link :to="`${article.slug}/`" class="text-blue-600 dark:text-blue-400 hover:underline mt-4">Читать</nuxt-link>-->
<!--            </div>-->
<!--          </div>-->
<!--        </div>-->
<!--      </div>-->
<!--    </section>-->
  </div>
</template>

<script>
export default {
  name: 'ArticlesPage',

  async asyncData({ $content }) {
    const articles = await $content('articles').fetch()
    return { articles }
  },

  data() {
    return {
      articles: []
    }
  },
}
</script>

<style lang="scss">

</style>
