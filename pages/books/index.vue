<template>
  <div class="books-page">
    <h1 class="text-2xl font-bold">Список книг</h1>
    <ul>
      <li v-for="(book, index) in books" :key="index">
        <nuxt-link :to="`${book.slug}/`">{{ book.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'BooksPage',

  async asyncData({ $content }) {
    const books = await $content('books').fetch()
    return { books }
  }
}
</script>

<style lang="scss">

</style>
