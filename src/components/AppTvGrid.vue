<script>

    import AppTvCard from './AppTvCard.vue'
    import { store } from '../store.js'

    export default {
        name: 'AppTvGrid',
        components: {
            AppTvCard
        },

        data() {
            return {
                store
            }
        },

    }

</script>

<template>

    <div class="container">
        <div class="title-container">
            <h2>Tv Series</h2>
        </div>
        <div class="row">
            <AppTvCard 
            v-for="tv in store.tvFound" 
            :key="tv.id" 
            :tvList="tv"></AppTvCard>
        </div>
    </div>
    


</template>

<style scoped lang="scss">

    .title-container {
        display: flex;
        justify-content: center;
    }

    .row {
            flex-wrap: wrap;
            gap: 10px;
        }

</style>