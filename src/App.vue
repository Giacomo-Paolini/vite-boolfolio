<script>
import AppMain from './components/AppMain.vue'
import {store} from '../src/data/store'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    AppMain
  },
  data() {
    return {
      store
    }
  },
  methods: {
    getProject() {
      axios.get(this.store.apiUrl).then((response) => {
        console.log(response);
        this.store.projects = response.data.data;
      });
    }
  },
  mounted() {
    this.getProject();
  }
}
</script>

<template>
  <AppMain />
</template>

<style scoped>

</style>
