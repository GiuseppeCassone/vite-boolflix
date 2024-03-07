<script>
  import axios from 'axios';
  import { store } from './store.js';

 import AppNav from './components/AppNav.vue';
 import AppMain from './components/AppMain.vue';

 export default {

      data() {

        return {
            store,
        }
      },

      components: {
        AppNav,
        AppMain,
      },

      methods: {

          searchMovies() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=39cad4f2c9bf7824ade8563d23362a6f&query=' + this.store.searchText).then(res => {
              this.store.filmList = res.data.results; 
              console.log(res.data.results)

              this.store.filmList.forEach(movie => {
                axios.get(`https://api.themoviedb.org/3/movie/${movie.id}/credits?api_key=39cad4f2c9bf7824ade8563d23362a6f`)
                  .then(res => {
                    this.store.filmCastList[movie.id] = res.data.cast;
                  })  
                });
            });

            axios.get('https://api.themoviedb.org/3/search/tv?api_key=39cad4f2c9bf7824ade8563d23362a6f&query=' + this.store.searchText).then(res => {
              this.store.tvSeriesList = res.data.results; 
              console.log(res.data.results)

              this.store.tvSeriesList.forEach(series => {
                axios.get(`https://api.themoviedb.org/3/movie/${series.id}/credits?api_key=39cad4f2c9bf7824ade8563d23362a6f`)
                  .then(res => {
                    this.store.filmCastList[series.id] = res.data.cast;
                  })  
                });
              
            });
          }
      }

}

</script>

<template>
  <AppNav @search="searchMovies()"></AppNav>
  <AppMain></AppMain>
</template>

<style lang="scss">

</style>
