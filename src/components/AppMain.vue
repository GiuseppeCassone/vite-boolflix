<script>

    import AppMovie from './AppMovie.vue';
    import AppSeries from './AppSeries.vue';

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
            AppSeries,
        },
    }

</script>

<template>
    <div class="container d-flex flex-wrap pt-5">
        <AppMovie class="mb-5" v-for="currentMovie in store.filmList" :movies="currentMovie"></AppMovie>
        
        <AppSeries v-for="currentSeries in store.tvSeriesList" :series="currentSeries"></AppSeries>
        
    </div>


</template>

<style lang="scss">


</style>