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
      img: 'https://image.tmdb.org/t/p/w780/'
    }
  },

  methods: {
    getRating (ratingValue) {
      const rating = Math.ceil(ratingValue / 2);
      console.log(rating)
      return rating;
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
      <li v-for="moviesItem in store.moviesList">
        <h2>Title: {{ moviesItem.title }}</h2>
        <img :src="this.img + moviesItem.backdrop_path" :alt="moviesItem.title">
        <div>
          <p>Original Title:{{ moviesItem.original_title }}</p>
          <p>Language: {{ moviesItem.original_language }} 
           <!--Da usare dopo // <lang-flag :iso="moviesItem.original_language"/> //-->
           <img :src="'/src/assets/img/' + moviesItem.original_language + '.png'" alt="" class="my-flag">
          </p>
          <p>Rating:
            <font-awesome-icon icon="fa-solid fa-star" v-for=" n in getRating(moviesItem.vote_average)" />
            <span v-if="getRating(moviesItem.vote_average) == 0">No ratings found</span>
          </p>
        </div>
      </li>
    </ul>

    <!--Serie TV-->
    <ul>
      <h1>Tv Series</h1>
      <h2> {{store.seriesList.length}} TV Series found</h2>
      <li v-for="seriesItem in store.seriesList">
        <h2>Title: {{ seriesItem.name }}</h2>
        <img :src="this.img + seriesItem.backdrop_path" alt="seriesItem.title">
        <div>
          <p>Original Title:{{ seriesItem.original_name }}</p>
          <p>Language: {{ seriesItem.original_language }} 
            <!--Da usare dopo // <lang-flag :iso="seriesItem.original_language"/> //-->
            <img :src="'/src/assets/img/' + seriesItem.original_language + '.png'" alt="" class="my-flag">
          </p>
          <p>Rating:
            <font-awesome-icon icon="fa-solid fa-star" v-for=" n in getRating(seriesItem.vote_average)" />
            <span v-if="getRating(seriesItem.vote_average) == 0">No ratings found</span>
          </p>
        </div>
      </li>
    </ul>
  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;

.main-wrapper {
  color: white;
}

ul {
  padding: 2rem 0;
  
}

.my-flag {
  width: 30px;
}

</style>
