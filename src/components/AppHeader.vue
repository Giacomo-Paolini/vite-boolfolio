<script>
export default {
    name: "AppHeader"
}
</script>

<template>
    <div class="container-fluid">
        <div class="container">
            <div class="row">
                <div class="d-flex justify-content-center align-items-center gap-5 p-3">
                    <router-link class="text-decoration-none" :to="{ name: 'home' }">
                        <h1 >Home</h1>
                    </router-link>

                    <router-link class="text-decoration-none" to="/projects">
                        <h1>Projects</h1>
                    </router-link>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

    h1 {
        color: white;
    }
    .container-fluid {
        background-color: black;
    }
</style>
