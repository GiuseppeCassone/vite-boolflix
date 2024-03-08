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
            <div class="cards-container d-flex flex-wrap w-100" v-if="store.filmList.length > 0">
                <AppCard v-for="currentMovie in store.filmList" :infos="currentMovie" :cast="store.filmCastList[currentMovie.id]"></AppCard>
            </div>
            <div class="no-results text-white" v-else>NESSUN FILM TROVATO CON QUESTA RICERCA</div>
        </div>

        <div class="d-flex flex-wrap">
            <h1 class="text-white w-100 ">Series</h1>
            <div class="cards-container d-flex flex-wrap w-100" v-if="store.tvSeriesList.length > 0">
                <AppCard v-for="currentSeries in store.tvSeriesList" :infos="currentSeries" :cast="store.tvSeriesCastList[currentSeries.id]"></AppCard>
            </div>
            <div class="no-results text-white" v-else>NESSUNA SERIE TV TROVATA CON QUESTA RICERCA</div>           
        </div>       
    </div>


</template>

<style lang="scss">


</style>