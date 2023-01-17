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
      moviesApiUri: 'https://api.themoviedb.org/3/search/movie?',
      seriesApiUri: 'https://api.themoviedb.org/3/search/tv?',
      genreList: 'https://api.themoviedb.org/3/genre/movie/list?',
    }
  },

  methods: {
    getMovies (searchedText) {
      console.log(searchedText);
      axios.get(this.moviesApiUri, {
        params: {
          api_key: this.apiKey,
          query: searchedText,
          
        }
      })


      .then((response) => {
        console.log(response.data.results);
        this.store.moviesList = response.data.results;
        
    })   
    },

    getSeries (searchedText) {
      console.log(searchedText);
      axios.get(this.seriesApiUri, {
        params: {
          api_key: this.apiKey,
          query: searchedText,
          
        }
      })


      .then((response) => {
        console.log(response.data.results);
        this.store.seriesList = response.data.results;
        
    })   
    },

    getGenres () {
      axios.get(this.genreList, {
        params: {
          api_key: this.apiKey,
        }
      })

      .then ((response) => {
        this.store.genresList =response.data.genres;
      })
    },

    searchAll(searchedText) {
      this.getSeries(searchedText);
      this.getMovies(searchedText);
    }
  },

  created() {
    this.getMovies();
    this.getSeries();
    this.getGenres();
  },
}

</script>

<template>

  <HeaderApp @searchedText="searchAll"/>
  <hr>
  <MainApp />

</template>

<style lang="scss">

@use './styles/general.scss' as *;
@use './styles/partials/_variables.scss' as *;


</style>
