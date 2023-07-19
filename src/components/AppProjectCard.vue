<script>

export default {
    name: "AppProjectCard",
    props: {
        project: Object,
    },
    data() {
        return {

        }
    },
}
</script>

<template>
    <div v-motion-slide-top>
        <div class="card gap-4 p-3">
            <h2>{{ project.title }}</h2>
            <div class="d-flex gap-3">
                <template v-for="technology in project.technologies">
                    <small>
                        {{ technology.name }}
                    </small>
                </template>
            </div>
            <img class="img-fluid" :src="'http://localhost:8000/storage/' + project.image" alt="">
            <p>{{ project.content }}</p>
        </div> 
    </div>
</template>

<style scoped>
.card {
    width: 100%;
}
</style>