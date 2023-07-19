<script>
export default {
    name: "AppHeader"
}
</script>

<template>
    <div class="container-fluid">
        <div class="container">
            <div class="row">
                <div class="d-flex justify-content-center align-items-center gap-5">
                    <router-link :to="{ name: 'home' }">
                        <h1>Home</h1>
                    </router-link>

                    <router-link to="/projects">
                        <h1>Projects</h1>
                    </router-link>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .container-fluid {
        background-color: lightblue;
    }
</style>
