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
    <div class="container pt-5">
        <div class="d-flex flex-wrap mb-5">
            <h1 class="text-white w-100">Movies</h1>
            <AppMovie v-for="currentMovie in store.filmList" :movies="currentMovie"></AppMovie>
        </div>

        <div class="d-flex flex-wrap">
            <h1 class="text-white w-100 ">Series</h1>
            <AppSeries v-for="currentSeries in store.tvSeriesList" :series="currentSeries"></AppSeries>           
        </div>       
    </div>


</template>

<style lang="scss">


</style>