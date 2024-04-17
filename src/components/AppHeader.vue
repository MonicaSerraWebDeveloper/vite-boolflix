<script>
    import { store } from '../store.js'

    export default {
        name: 'AppHeader',
        data() {
            return {
                store
            }
        }
    }

</script>

<template>

    <div class="container">
        <div class="row">
            <input v-model="store.querySearched" type="text">
            <button @click="$emit('fireResults')">Click</button>
        </div>
    </div>

</template>

<style scoped lang="scss">


</style>