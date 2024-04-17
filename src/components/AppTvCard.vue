<script>

    export default {
        name: 'AppTvCard',
        props: {
            tvList: Object
        },

        methods: {
            getFlags() {

            if(this.tvList.original_language === 'en') {
                return new URL(`../assets/flag/uk-flag.png`, import.meta.url).href
            } else if (this.tvList.original_language === 'it') {
                return new URL(`../assets/flag/ita-flag.png`, import.meta.url).href
            } else if (this.tvList.original_language === 'fr') {
                return new URL(`../assets/flag/france-flag.png`, import.meta.url).href
            } else if (this.tvList.original_language === 'es') {
                return new URL(`../assets/flag/spain-flag.png`, import.meta.url).href
            }
            }
        }
    }

</script>

<template>

    <div class="container-card-tv">
        <img 
        class="cover-tv" 
        :src="'https://image.tmdb.org/t/p/w342' + tvList.poster_path" 
        v-if="tvList.poster_path" 
        :alt="tvList.title"
        >
        <div class="info-container">
            <h3>{{ tvList.name}}</h3>
            <h3>{{ tvList.original_name }}</h3>
            <div>
                <img :src="getFlags()" v-if="getFlags()" :alt="tvList.original_language">
                <div v-else>{{ tvList.original_language }}</div>
            </div>
            <div class="stars-cotnainer">
                <i v-for="star in Math.ceil(tvList.vote_average / 2)" class="fa-solid fa-star"></i>
                <i v-for="emptyStar in 5 - Math.ceil(tvList.vote_average / 2)" class="fa-regular fa-star"></i>
            </div>
        </div>
    </div>

</template>

<style scoped lang="scss">

    .container-card-tv {
        border: 2px solid blue;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        width: calc((100% / 5) - 10px);
        cursor: pointer;

        .cover-tv {
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