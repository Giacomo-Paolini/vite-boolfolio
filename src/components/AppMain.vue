<script>
import axios from 'axios';

export default {
  name: "AppMain",
  data() {
      return {
        apiUrl: "http://localhost:8000/api/projects",
        projects: [],
      }
  },
  methods: {
    getProject() {
      axios.get(this.apiUrl).then((response) => {
        console.log(response.data);
        this.projects = response.data.data;
      });
    }
  },
  mounted() {
    this.getProject();
  }
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="d-flex flex-wrap justify-content-center align-items-center gap-3">
        <div class="card" v-for="project in projects">
          <h1>
            {{ project.title }}
          </h1>
          <p>
            {{ project.content }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.card {
  width: calc(100% / 4);
}
</style>
