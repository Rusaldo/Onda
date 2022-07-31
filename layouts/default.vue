<template>
  <div>
    <AppHeader />
    <AppBreadcrumbs />
    <nuxt />
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader/AppHeader"
import AppBreadcrumbs from "@/components/AppBreadcrumbs/AppBreadcrumbs"
import AppFooter from "@/components/AppFooter/AppFooter"

export default {
  name: 'DefaultLayout',

  components: {
    AppFooter,
    AppBreadcrumbs,
    AppHeader
  }
}
</script>
