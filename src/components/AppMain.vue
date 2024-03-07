<script>

    import AppCard from './AppCard.vue';

    import {store} from '../store.js';



    export default {
        name: 'AppMain',

        data() {

            return {
                store,
            }
        },

        components: {
            AppCard,
        },
    }

</script>

<template>
    <div class="container pt-5">
        <div class="d-flex flex-wrap mb-5">
            <h1 class="text-white w-100">Movies</h1>
            <AppCard v-for="currentMovie in store.filmList" :infos="currentMovie" :cast="store.filmCastList[currentMovie.id]"></AppCard>
        </div>

        <div class="d-flex flex-wrap">
            <h1 class="text-white w-100 ">Series</h1>
            <AppCard v-for="currentSeries in store.tvSeriesList" :infos="currentSeries" :cast="store.tvSeriesCastList[currentSeries.id]"></AppCard>           
        </div>       
    </div>


</template>

<style lang="scss">


</style>