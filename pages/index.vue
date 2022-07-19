<template>
  <div>
    <h1 class="text-2xl font-bold">Главная</h1>
    <h2>Навигация</h2>
    <ul>
      <li>
        <nuxt-link to="/articles/">Статьи</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
