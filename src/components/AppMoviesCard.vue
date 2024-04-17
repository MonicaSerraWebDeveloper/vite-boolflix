<script>

    export default {
        name: 'AppMoviesCard',
        props: {
            moviesList: Object
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
            },

            getStarsVote() {
                const voteInStars = Math.ceil(moviesList.vote_average / 2)
                return voteInStars
            },

            getEmptyStars() {
                return 5 - (Math.ceil(moviesList.vote_average / 2))
            }
        }
    }

</script>

<template>
    <div class="container-card">
        <img 
        class="cover-movie" 
        :src="'https://image.tmdb.org/t/p/w342' + moviesList.poster_path" 
        v-if="moviesList.poster_path" 
        :alt="moviesList.title"
        >
        <div class="info-container">
            <h3>{{ moviesList.title }}</h3>
            <h3>{{ moviesList.original_title }}</h3>
            <div>
                <img :src="getFlags()" v-if="getFlags()" :alt="moviesList.original_language">
                <div v-else>{{ moviesList.original_language }}</div>
            </div>
            <div class="stars-cotnainer">
                <i v-for="star in Math.ceil(moviesList.vote_average / 2)" class="fa-solid fa-star"></i>
                <i v-for="emptyStar in 5 - Math.ceil(moviesList.vote_average / 2)" class="fa-regular fa-star"></i>
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
        width: calc((100% / 5) - 10px);
        cursor: pointer;

        .cover-movie {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top;
        }

        .info-container {
            padding: 10px;
            img {
                width: 20px;
            }

            i {
                color: gold; 
            }
        }

    }

   

</style>