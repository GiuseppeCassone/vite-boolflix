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

      created() {
          axios.get('https://api.themoviedb.org/3/movie/popular?api_key=39cad4f2c9bf7824ade8563d23362a6f').then(res => {
            this.store.filmList = res.data.results;
            this.getCastMembers();
            this.getGenres();
          });

          axios.get('https://api.themoviedb.org/3/tv/popular?api_key=39cad4f2c9bf7824ade8563d23362a6f').then(res => {
            this.store.tvSeriesList = res.data.results;
            this.getCastMembers();
            this.getGenres();
          });
      },

      methods: {

          searchMovies() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=39cad4f2c9bf7824ade8563d23362a6f&query=' + this.store.searchText).then(res => {
              this.store.filmList = res.data.results; 
              // console.log(res.data.results)
              this.getCastMembers();
              this.getGenres();
            });
                
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=39cad4f2c9bf7824ade8563d23362a6f&query=' + this.store.searchText).then(res => {
              this.store.tvSeriesList = res.data.results; 
              // console.log(res.data.results)
              this.getCastMembers();
              this.getGenres();
              
            });
          },

          getCastMembers() {
              this.store.filmList.forEach(movie => {
                axios.get(`https://api.themoviedb.org/3/movie/${movie.id}/credits?api_key=39cad4f2c9bf7824ade8563d23362a6f`)
                  .then(res => {
                    this.store.filmCastList[movie.id] = res.data.cast;
                  })  
              });

              this.store.tvSeriesList.forEach(series => {
                axios.get(`https://api.themoviedb.org/3/tv/${series.id}/credits?api_key=39cad4f2c9bf7824ade8563d23362a6f`)
                  .then(res => {
                    this.store.tvSeriesCastList[series.id] = res.data.cast;
                  })  
              });
          },

          getGenres() {
              axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=39cad4f2c9bf7824ade8563d23362a6f').then(res => {
                this.store.filmGenres = res.data.genres;
                
              });
              
              axios.get('https://api.themoviedb.org/3/genre/tv/list?api_key=39cad4f2c9bf7824ade8563d23362a6f').then(res => {
                this.store.tvSeriesGenres = res.data.genres;
                
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
