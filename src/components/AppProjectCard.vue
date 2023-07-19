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
    <h1>{{ project.title }}</h1>
    <small>{{ project.technologies.name}}</small>
    <p>{{ project.content }}</p>
</template>