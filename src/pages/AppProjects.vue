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
        <div class="row">
            <h1 class="text-center my-3">
                Projects
            </h1>
            <div class="d-flex flex-wrap justify-content-center gap-3 my-4">
                <template v-for="project in projects">
                <div class="card gap-4 p-3">
                    <AppProjectCard :project="project" />
                </div>
                </template>
            </div>
            <div class="d-flex justify-content-center align-items-center gap-5 my-4">
                <a class="button" @click="getProjectPrevPage">Pagina precedente</a>
                <a class="button" @click="getProject(pageNumber)" v-for="pageNumber in projectTotalPage">{{ pageNumber }}</a>
                <a class="button" @click="getProjectNextPage">Pagina successiva</a>
            </div>
        </div>

    </div>
</template>

<style scoped>

.card {
    width: calc(100% / 2 - 20px);
}

a {
    cursor: pointer;
}
</style>
