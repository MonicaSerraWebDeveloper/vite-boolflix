<script>

    import AppMoviesCard from './AppMoviesCard.vue'

    export default {
        name: 'AppMoviesGrid',
        components: {
            AppMoviesCard
        }
    }

</script>

<template>

    <div class="container">
        <div class="row">
            <AppMoviesCard></AppMoviesCard>
        </div>
    </div>
    
</template>

<style scoped lang="scss">


</style>