<template>
  <header class="app-header">
    <nav class="bg-gray-800">
      <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
        <div class="relative flex items-center justify-between h-16">
          <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
            <button type="button"
                    class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
                    aria-controls="mobile-menu"
                    :aria-expanded="isMenuOpen"
                    @click="isMenuOpen = !isMenuOpen">
              <span class="sr-only">Open main menu</span>
              <svg v-if="isMenuOpen" class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
              </svg>
              <svg v-else class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
              </svg>
            </button>
          </div>

          <div class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start">
            <div class="flex-shrink-0 flex items-center">
              <img class="block lg:hidden h-8 w-auto" src="https://tailwindui.com/img/logos/workflow-mark-indigo-500.svg" alt="Workflow">
              <img class="hidden lg:block h-8 w-auto" src="https://tailwindui.com/img/logos/workflow-logo-indigo-500-mark-white-text.svg" alt="Workflow">
            </div>
            <div class="hidden sm:block sm:ml-6">
              <div class="flex space-x-4">
                <nuxt-link v-for="(item, index) in nav"
                           :key="index"
                           :to="item.path"
                           class="px-3 py-2 rounded-md text-sm font-medium"
                           :class="{
                             'bg-gray-900 text-white': item.path === $route.path,
                             'text-gray-300 hover:bg-gray-700 hover:text-white': item.path !== $route.path
                           }"
                           aria-current="page">
                  {{ item.name }}
                </nuxt-link>
              </div>
            </div>
          </div>

          <div class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
            <div class="ml-3 relative">
              <div>
                <button type="button"
                        id="user-menu-button"
                        class="bg-gray-800 flex text-sm rounded-full focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white"
                        :aria-expanded="isProfileMenuOpen"
                        aria-haspopup="true"
                        @click="isProfileMenuOpen = !isProfileMenuOpen">
                  <span class="sr-only">Open user menu</span>
                  <img class="h-8 w-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
                </button>
              </div>
              <div v-if="isProfileMenuOpen" class="origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg py-1 bg-white ring-1 ring-black ring-opacity-5 focus:outline-none" role="menu" aria-orientation="vertical" aria-labelledby="user-menu-button" tabindex="-1">
                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-0">Your Profile</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-1">Settings</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-2">Sign out</a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div v-if="isMenuOpen"
           id="mobile-menu"
           class="sm:hidden">
        <div class="px-2 pt-2 pb-3 space-y-1">
          <nuxt-link v-for="(item, index) in nav"
                     :key="index"
                     :to="item.to"
                     class="block px-3 py-2 rounded-md text-base font-medium"
                     :class="{
                       'bg-gray-900 text-white': item.path === $route.path,
                       'text-gray-300 hover:bg-gray-700 hover:text-white': item.path !== $route.path,
                     }"
                     aria-current="page">
            {{ item.name }}
          </nuxt-link>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',

  data() {
    return {
      isMenuOpen: false,
      isProfileMenuOpen: false
    }
  },

  computed: {
    nav() {
      return [
        {
          name: 'Главная',
          path: '/'
        },
        {
          name: 'Статьи',
          path: '/articles/'
        },
        {
          name: 'Книги',
          path: '/books/'
        },
        {
          name: 'Аудио',
          path: '/audio/'
        },
        {
          name: 'Контакты',
          path: '/contact/'
        }
      ]
    }
  }
}
</script>
