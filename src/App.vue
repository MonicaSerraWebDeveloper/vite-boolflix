<script>
    import AppHeader from './components/AppHeader.vue'
    import AppMoviesGrid from './components/AppMoviesGrid.vue'
    import AppTvGrid from './components/AppTvGrid.vue'
    import { store } from './store.js'
    import axios from 'axios'

    export default {
        components: {
            AppHeader,
            AppMoviesGrid,
            AppTvGrid
        }
    }


</script>

<template>

    <AppHeader></AppHeader>
    <main>
        <AppMoviesGrid></AppMoviesGrid>
        <AppTvGrid></AppTvGrid>
    </main>

</template>

<style lang="scss">

</style>
