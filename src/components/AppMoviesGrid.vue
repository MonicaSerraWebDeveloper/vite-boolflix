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
        <div class="title-container">
            <h2>Movies</h2>
        </div>
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

    .title-container {
            display: flex;
            justify-content: center;
            padding: 50px 0;

            h2 {
            font-size: 40px;
        }
        }

    .row {
        flex-wrap: wrap;
        gap: 10px;
    }

</style>