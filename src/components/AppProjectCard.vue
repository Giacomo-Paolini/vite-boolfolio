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
    <h2>{{ project.title }}</h2>
    <div class="d-flex gap-3">
        <template v-for="technology in project.technologies">
            <small>
                {{ technology.name }}
            </small>
        </template>
    </div>
    <img :src="'http://localhost:8000/storage/' + project.image" alt="">
    <p>{{ project.content }}</p>
</template>