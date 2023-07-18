<script>
import AppHeader from './components/AppHeader.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
  },
  data() {
    return {

    }
  }
}

</script>

<template>
  <AppHeader />
  <router-view></router-view>
</template>

<style scoped>

</style>
