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
        },

        data() {
            return {
                store
            }
        },

        methods: {
            getMoviesFromApi() {
                const queryParams = {
                    api_key: 'e95f337e5ac359a9815573d658c29bd6',
                    query: 'taylor'
                };

                // if(store.querySearched !== '') {
                //     queryParams.query = store.querySearched
                // }

                axios.get('https://api.themoviedb.org/3/search/movie', {
                    params: queryParams
                }).then((response) => {
                    store.moviesFound = response.data.results
                    console.log(response.data.results);
                    
                })
            }
        },
        mounted() {
            this.getMoviesFromApi()
        }
    }


</script>

<template>

    <AppHeader @fireResults="console.log('monica')"></AppHeader>
    <main>
        <AppMoviesGrid></AppMoviesGrid>
        <AppTvGrid></AppTvGrid>
    </main>

</template>

<style lang="scss">

    @use './style/generic'

</style>
