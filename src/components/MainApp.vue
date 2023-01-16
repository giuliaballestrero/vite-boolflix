<script>
import { store } from '../store.js';
import LangFlag from 'vue-lang-code-flags';
console.log(store);
import MovieComponent from './MovieComponent.vue';

export default {

  name: 'MainApp',

  components:  {
    MovieComponent,
    LangFlag,
  },

  data () {
    return {
      store,
    }
  },
}

</script>

<template>
  <section class="main-wrapper">
    <!--Film-->
    <ul>
      <h1>Movies</h1>
      <h2> {{store.moviesList.length}} Movies found</h2>
      <li v-for="movieItem in store.moviesList">
        <h2>Title: {{ movieItem.title }}</h2>
        <div>
          <p>Original Title:{{ movieItem.original_title }}</p>
          <p>Language: {{ movieItem.original_language }} <lang-flag :iso="movieItem.original_language"/> </p>
          <p>Rating: {{ movieItem.vote_average }} stars</p>
        </div>
      </li>
    </ul>

    <!--Serie TV-->
    <ul>
      <h1>Tv Series</h1>
      <h2> {{store.seriesList.length}} TV Series found</h2>
      <li v-for="seriesItem in store.seriesList">
        <h2>Title: {{ seriesItem.name }}</h2>
        <div>
          <p>Original Title:{{ seriesItem.original_name }}</p>
          <p>Language: {{ seriesItem.original_language }} <lang-flag :iso="seriesItem.original_language"/></p>
          <p>Rating: {{ seriesItem.vote_average }} stars</p>
        </div>
      </li>
    </ul>
  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;

ul {
  padding: 2rem 0;
}

lang-flag {
  font-size: 2rem;
}

</style>
