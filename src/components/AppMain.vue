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

    <AppMovie v-for="currentMovie in store.filmList" :movies="currentMovie"></AppMovie>


</template>

<style lang="scss">

</style>