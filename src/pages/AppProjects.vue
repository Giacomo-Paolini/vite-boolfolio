<script>
import AppProjectCard from "../components/AppProjectCard.vue";
import axios from 'axios'

export default {
    name: "AppMain",
    components: {
        AppProjectCard,
    },
    data() {
        return {
        apiUrl: "http://localhost:8000/api/projects",
        projects: [],
        }
    },
    methods: {
        getProject() {
        axios.get(this.apiUrl).then((response) => {
            console.log(response);
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
        <h1 class="text-center my-3">
            Projects
        </h1>
        <div class="d-flex flex-wrap justify-content-center gap-3">
            <template v-for="project in projects">
            <div class="card gap-4 p-3">
                <AppProjectCard :project="project" />
            </div>
            </template>
        </div>
        </div>
    </div>
</template>

<style scoped>

.card {
    width: calc(100% / 4);
}
</style>
