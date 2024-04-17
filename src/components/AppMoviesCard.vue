<script>

    import { store } from '../store.js'

    export default {
        name: 'AppMoviesCard',
        props: {
            moviesList: Object
        },

        data() {
            return {
                store
            }
        }
    }

</script>

<template>
    <div class="container-card">
        <div class="image-placeholder"></div>
        <div class="info-container">
            <h3>{{ moviesList.title }}</h3>
            <h3>{{ moviesList.original_title }}</h3>
            <div>{{ moviesList.original_language }}</div>
            <div>{{ Math.ceil(moviesList.vote_average) }}</div>
        </div>
    </div>

</template>

<style scoped lang="scss">
    .container-card {
        border: 2px solid green;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 20px;
        width: calc((100% / 5) - 10px);

        .image-placeholder {
        width: 100%;
        height: 120px;
        border: 2px solid red;
    }

    }

   

</style>