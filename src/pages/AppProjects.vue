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
            apiUrl: "http://localhost:8000/api/",
            projects: [],
            projectCurrentPage: 0,
            projectTotalPage: 0,
        }
    },
    methods: {
        getProjectFirstPage() {
            axios.get(this.apiUrl + "projects").then(response => {
                    console.log(response);
                    this.projects = response.data.data.data;
                    this.projectCurrentPage = response.data.data.current_page;
                    this.projectTotalPage = response.data.data.last_page;
                });
        },
        getProject(pageNumber) {
            if(pageNumber && pageNumber > 0 && pageNumber <= this.projectTotalPage) {

                let config = {
                    params: {
                        page: pageNumber
                    }
                };
                axios.get(this.apiUrl + "projects", config).then(response => {
                    console.log(response);
                    this.projects = response.data.data.data;
                    this.projectCurrentPage = response.data.data.current_page;
                    this.projectTotalPage = response.data.data.last_page;
                });
            } else {
                console.error("Non ci sono più pagine");
            }
        },
        getProjectPrevPage() {
            this.getProject(  this.projectCurrentPage - 1 );
        },
        getProjectNextPage() {
            this.getProject( this.projectCurrentPage + 1 );
        },
    },
    mounted() {
        this.getProjectFirstPage();
    }
}
</script>

<template>
    <div class="container">
        <h1 class="text-center my-3">
            Projects
        </h1>
        <div class="row row-cols-2">
            <div class="my-3" v-for="project in projects">
                <AppProjectCard :project="project" />
            </div>
        </div>
        <div class="d-flex justify-content-center align-items-center gap-5 my-4">
            <a class="button" @click="getProjectPrevPage">Pagina precedente</a>
            <a class="button" @click="getProject(pageNumber)" v-for="pageNumber in projectTotalPage">{{ pageNumber }}</a>
            <a class="button" @click="getProjectNextPage">Pagina successiva</a>
        </div>

    </div>
</template>

<style scoped>

a {
    cursor: pointer;
}
</style>
