<template>
  <div class="app-breadcrumbs flex items-center py-4 overflow-y-auto whitespace-nowrap">
    <a href="#" class="text-gray-600 dark:text-gray-200">
      <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 20 20" fill="currentColor">
        <path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" />
      </svg>
    </a>

    <span class="mx-5 text-gray-500 dark:text-gray-300">
            /
        </span>

    <a href="#" class="text-gray-600 dark:text-gray-200 hover:underline">
      Account
    </a>

    <span class="mx-5 text-gray-500 dark:text-gray-300">
            /
        </span>

    <a href="#" class="text-gray-600 dark:text-gray-200 hover:underline">
      Profile
    </a>

    <span class="mx-5 text-gray-500 dark:text-gray-300">
            /
        </span>

    <a href="#" class="text-blue-600 dark:text-blue-400 hover:underline">
      Settings
    </a>
  </div>
</template>

<script>
export default {
  name: 'AppBreadcrumbs',

  computed: {
    breadcrumbsLinks() {
      let tmp = []
      if (this.$route.matched) {
        this.$route.matched.forEach(link => {
          tmp.push(Object.assign({meta: {title: 'Title not found in meta'}}, link))
        })
      }
      if (tmp.length === 0) {
        tmp.push({path: '/', meta: {title: 'Home'}})
      }
      return tmp
    }
  }
}
</script>
