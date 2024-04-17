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

    <header>
        <div class="container">
            <div class="title-container">
                <h1>BoolFlix</h1>
            </div>
            <div class="row">
                <input v-model="store.querySearched" type="text">
                <button @click="$emit('fireResults')">Cerca</button>
            </div>
        </div>
    </header>
    

</template>

<style scoped lang="scss">

    header {
        background-color: #000;
        padding: 20px 0;

            .title-container {
            display: flex;
            justify-content: center;

            h1 {
                color: red;
            }
        }

        .row {
            gap: 10px;
            input {
            width: 500px;
            height: 40px;
            border-radius: 20px;
            border: 1px solid #fff;
            padding: 20px;
            font-family: "Sen", sans-serif;
            font-size: 16px;
            outline: none;
        }

            button {
                width: 100px;
                height: 40px;
                border-radius: 20px;
                border: 1px solid #ccc;
                background-color: #ccc;
                font-family: "Sen", sans-serif;
                font-size: 16px;
        }
        }

        

    }

    

</style>