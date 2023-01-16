<script>
import axios from 'axios';
import { store } from './store.js';
import MainApp from './components/MainApp.vue';
import HeaderApp from './components/HeaderApp.vue';

export default {
  components: {
    MainApp,
    HeaderApp,
  },

  data () {
    return {
      store,
      apiKey: 'c065d34d7a17aa24d73d1521ae673433',
      apiUri: 'https://api.themoviedb.org/3/search/movie?',
    }
  },

  methods: {
    getMovies (searchedMovie) {
      console.log(searchedMovie);
      axios.get(this.apiUri, {
        params: {
          api_key: this.apiKey,
          query: searchedMovie,
          
        }
      })


      .then((response) => {
        console.log(response.data.results);
        this.store.moviesList = response.data.results;
        
    })   
    }
  },

  created() {
    this.getMovies();
  },
}

</script>

<template>

  <HeaderApp @searchMovie="getMovies"/>
  
  <MainApp />

</template>

<style lang="scss">

@use './styles/general.scss' as *;
@use './styles/partials/_variables.scss' as *;

</style>
