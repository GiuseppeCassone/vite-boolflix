<script>

    import AppMovie from './AppMovie.vue';

    import {store} from '../store.js';



    export default {
        name: 'AppMain',

        data() {

            return {
                store,
            }
        },

        components: {
            AppMovie,
        },
    }

</script>

<template>
    <div class="container d-flex flex-wrap pt-5">
        <AppMovie v-for="currentMovie in store.filmList" :movies="currentMovie"></AppMovie>
        
    </div>


</template>

<style lang="scss">


</style>