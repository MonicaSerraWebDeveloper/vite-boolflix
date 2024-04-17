<script>
    import AppHeader from './components/AppHeader.vue'
    import AppMoviesGrid from './components/AppMoviesGrid.vue'
    import AppTvGrid from './components/AppTvGrid.vue'
    import { store } from './store.js'
    import axios from 'axios'
    import AppHero from './components/AppHero.vue'

    export default {
        components: {
            AppHeader,
            AppMoviesGrid,
            AppTvGrid,
            AppHero
        },

        data() {
            return {
                store,
                isShowed: true,
            }
        },

        methods: {

            searchResult() {
                if(store.querySearched !== '') {
                    this.isShowed = false
                } else {
                    this.isShowed = true
                }
            },

            getMoviesFromApi() {

                const queryParams = {
                    api_key: 'e95f337e5ac359a9815573d658c29bd6',
                };

                if(store.querySearched !== '') {
                    queryParams.query = store.querySearched
                }

                axios.get('https://api.themoviedb.org/3/search/movie', {
                    params: queryParams
                }).then((response) => {
                    store.moviesFound = response.data.results                    
                })
            },

            getTvSeriesFromApi() {

                const queryParamsTv = {
                    api_key: 'e95f337e5ac359a9815573d658c29bd6',
                }

                if(store.querySearched !== '') {
                    queryParamsTv.query = store.querySearched
                }

                axios.get('https://api.themoviedb.org/3/search/tv', {
                    params: queryParamsTv
                }).then((response) => {
                    store.tvFound = response.data.results
                    console.log(response.data.results);
                })
            }
        },
        mounted() {
            this.getMoviesFromApi(),
            this.getTvSeriesFromApi(),
            this.searchResult()
        }
    }


</script>

<template>

    <AppHeader 
    @fireResults="getMoviesFromApi(); getTvSeriesFromApi(); searchResult()" 
    @enterResult="getMoviesFromApi(); getTvSeriesFromApi(); searchResult()"></AppHeader>
    <main>

        <AppHero v-if="isShowed"></AppHero>
        <div v-else-if="!isShowed">
            <AppMoviesGrid></AppMoviesGrid>
            <AppTvGrid></AppTvGrid>
        </div>
        
    </main>

</template>

<style lang="scss">

    @use './style/generic';

    main {
        padding-bottom: 100px;
    }

</style>
