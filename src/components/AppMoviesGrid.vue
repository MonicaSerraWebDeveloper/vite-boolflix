<script>

    import AppMoviesCard from './AppMoviesCard.vue'
    import { store } from '../store.js'

    export default {
        name: 'AppMoviesGrid',
        components: {
            AppMoviesCard
        },
        data() {
            return {
                store
            }
        }
    }

</script>

<template>

    <div class="container">
        <div class="row">
            <AppMoviesCard 
            v-for="movie in store.moviesFound" 
            :key="movie.id" 
            :moviesList="movie"
            ></AppMoviesCard>
        </div>
    </div>
    
</template>

<style scoped lang="scss">

    .row {
        flex-wrap: wrap;
        gap: 10px;
    }

</style>