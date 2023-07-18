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
    <p>{{ project.content }}</p>
</template>