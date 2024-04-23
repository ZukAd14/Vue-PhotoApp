<template>
  <div id="app">
  <div class="container p-p-4">

    <app-header />

    <main>
      <router-view v-slot="{ Component }">
        <SlideFadeAnimation>
          <component :is="Component" :key="$route.fullPath"/>
        </SlideFadeAnimation>
      </router-view>
    </main>

    <app-footer />

  </div>
</div>
</template>

<script>
import AppHeader from '@/components/layout/theHeader'
import AppFooter from '@/components/layout/theFooter'
import { mapActions } from 'vuex'

export default {
  name: 'App',
  components: { AppHeader, AppFooter },
  methods: {
    ...mapActions('Categories', ['fetchCategories'])
  },
  created () {
    this.fetchCategories()
  }
}
</script>
