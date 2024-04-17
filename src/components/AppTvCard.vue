<script>

    export default {
        name: 'AppTvCard',
        props: {
            tvList: Object
        }
    }

</script>

<template>

    <div class="container-card-tv">
        <div class="image-placeholder"></div>
        <div class="info-container">
            <h3>{{ tvList.name}}</h3>
            <h3>{{ tvList.original_name }}</h3>
            <div>{{ tvList.original_language }}</div>
            <div>{{ Math.ceil(tvList.vote_average) }}</div>
        </div>
    </div>

</template>

<style scoped lang="scss">

    .container-card-tv {
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