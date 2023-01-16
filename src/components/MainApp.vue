<script>
import { store } from '../store.js';
console.log(store);
import MovieComponent from './MovieComponent.vue';

export default {

  name: 'MainApp',

  components:  {
    MovieComponent,
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
    <h2> {{store.moviesList.length}} Movies found</h2>
    <ul>
      <li v-for="movieItem in store.moviesList">
        <h2>Title: {{ movieItem.title }}</h2>
        <div>
          <p>Original Title:{{ movieItem.original_title }}</p>
          <p>Language: {{ movieItem.original_language }}</p>
          <p>Rating: {{ movieItem.vote_average }} stars</p>
        </div>

      </li>
    </ul>
  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;

</style>
