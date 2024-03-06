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

      created() {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=39cad4f2c9bf7824ade8563d23362a6f&query=ritorno+al+futuro').then(res => {
          this.store.filmList = res.data.results;
          console.log(res.data.results);
        })
      },

      components: {
        AppNav,
        AppMain,
      }

}

</script>

<template>
  <AppNav></AppNav>
</template>

<style lang="scss">

</style>
