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
        <div class="hover-card">
            <div class="info-container">
                <h3><strong>Titolo:</strong>  {{ moviesList.title }}</h3>
                <h3><strong>Titolo Originale:</strong> {{ moviesList.original_title }}</h3>
                <div>
                    <img :src="getFlags()" v-if="getFlags()" :alt="moviesList.original_language">
                    <div v-else>{{ moviesList.original_language }}</div>
                </div>
                <div class="stars-cotnainer">
                    <span><strong>Voto: </strong></span>
                    <i v-for="star in Math.ceil(moviesList.vote_average / 2)" class="fa-solid fa-star"></i>
                    <i v-for="emptyStar in 5 - Math.ceil(moviesList.vote_average / 2)" class="fa-regular fa-star"></i>
                </div>
            
            </div>
        </div>

    </div>
    
</template>

<style scoped lang="scss">

   
    .container-card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        width: calc((100% / 5) - 10px);
        cursor: pointer;
        position: relative;

        .cover-movie {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top;

            &:hover {
            opacity: 0;
            }
        }
    }
    .hover-card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: left;
        line-height: 30px;
        background-color: #000;
        width: 100%;
        height: 100%;
        cursor: pointer;
        position: absolute;
        top: 0;
        right: 0;
        opacity: 0;
        transition: opacity 0.3s ease;

        &:hover {
            opacity: 1;
        }

        h3 {
            font-weight: 300;
            font-size: 16px;
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