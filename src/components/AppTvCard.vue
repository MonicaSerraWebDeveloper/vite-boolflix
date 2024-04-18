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
        <div class="hover-card">
            <div class="info-container">
                <h3><strong>Titolo:</strong> {{ tvList.name}}</h3>
                <h3><strong>Titolo Originale:</strong> {{ tvList.original_name }}</h3>
                <div>
                    <img :src="getFlags()" v-if="getFlags()" :alt="tvList.original_language">
                    <div v-else>{{ tvList.original_language }}</div>
                </div>
                <div class="stars-cotnainer">
                    <span><strong>Voto: </strong></span>
                    <i v-for="star in Math.ceil(tvList.vote_average / 2)" class="fa-solid fa-star"></i>
                    <i v-for="emptyStar in 5 - Math.ceil(tvList.vote_average / 2)" class="fa-regular fa-star"></i>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped lang="scss">

    .container-card-tv {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        width: calc((100% / 5) - 10px);
        cursor: pointer;
        position: relative;

        .cover-tv {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top;
        }

    }

    .hover-card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: left;
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
            padding: 20px;
            height: 100%;
            display: flex;
            flex-direction: column;
            gap: 15px;
            justify-content: center;

            img {
                width: 20px;
            }

            i {
                color: gold;
            }
        }
    }

</style>