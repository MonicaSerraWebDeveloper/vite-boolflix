<script>

    import { store } from '../store.js'

    export default {
        name: 'AppMoviesCard',
        props: {
            moviesList: Object
        },

        data() {
            return {
                store,

                    flags: [
                    {
                        ita: '/ita-flag.png'
                    },
                    {
                        france: '/france-flag.png'
                    },
                    {
                        spain: '/spain-flag.png'
                    },
                    {
                        uk: '/uk-flag.png'
                    }
                ]
            }
        },

        methods: {

            getFlags() {

                if(this.moviesList.original_language === 'en') {
                    return new URL(`../assets/flag/uk-flag.png`, import.meta.url).href
                } else if (this.moviesList.original_language === 'it') {
                    return new URL(`../assets/flag/ita-flag.png`, import.meta.url).href
                } else if (this.moviesList.original_language === 'fr') {
                    return new URL(`../assets/flag/france-flag.png`, import.meta.url).href
                } else if (this.moviesList.original_language === 'es') {
                    return new URL(`../assets/flag/spain-flag.png`, import.meta.url).href
                }
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
            <div>
                
                <img :src="getFlags()" v-if="getFlags()" alt="">
                
                <div v-else>{{ moviesList.original_language }}</div>
            </div>
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

        .info-container {
            img {
                width: 20px;
            }
        }

    }

   

</style>