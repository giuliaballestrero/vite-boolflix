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
      img: 'https://image.tmdb.org/t/p/w342/'
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
    <h1>Movies</h1>
    <h2> {{store.moviesList.length}} Movies found</h2>
    <ul>
        <li v-for="moviesItem in store.moviesList" class="single-card">
          <h2>Title: {{ moviesItem.title }}</h2>
          <img :src="this.img + moviesItem.poster_path" :alt="moviesItem.title">
          <div>
            <h3>Original Title:{{ moviesItem.original_title }}</h3>
            <h4>Language: {{ moviesItem.original_language }} 
            <lang-flag :iso="moviesItem.original_language"/>
            <!--Alternativa<img :src="'/src/assets/img/' + moviesItem.original_language + '.png'" alt="" class="my-flag">-->
            </h4>
            <p>Rating:
              <font-awesome-icon icon="fa-solid fa-star" v-for=" n in getRating(moviesItem.vote_average)" />
              <span v-if="getRating(moviesItem.vote_average) == 0">No ratings found</span>
            </p>
          </div>
        </li>
    </ul>
    <hr>
    <!--Serie TV-->
    <h1>Tv Series</h1>
    <h2> {{store.seriesList.length}} TV Series found</h2>
    <ul>
        <li v-for="seriesItem in store.seriesList" class="single-card">
          <h2>Title: {{ seriesItem.name }}</h2>
          <img :src="this.img + seriesItem.poster_path" alt="seriesItem.title">
          <div>
            <h3>Original Title:{{ seriesItem.original_name }}</h3>
            <h4>Language: {{ seriesItem.original_language }} 
              <lang-flag :iso="seriesItem.original_language"/> 
              <!--Alternativa img locali// <img :src="'/src/assets/img/' + seriesItem.original_language + '.png'" alt="" class="my-flag">//-->
            </h4>
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
  padding: 0 2rem;
  text-align: center;
  h1,
  h2 {
    text-transform: uppercase;
  }

  h1 {
  padding-top: 3rem;
  font-size: 3rem;
  }

}

.single-card {
    width: calc(100% / 5 - 1rem);
    margin: 2rem .5rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border: 1px solid white;

    img {
      width: 100%;
      height: 100%;
    }

    h2,
    h3,
    h4,
    p {
      display: none;
    }
    

    h2 {
      padding: 2rem;
    }

    h3 {
      color: grey;
    }

    p {
      font-size: 1.5rem;
      padding: 1rem;
    }

}

ul {
  padding: 2rem 0;
  display: flex;
  flex-wrap: wrap;
  
}

/*.my-flag {
  width: 30px;
}*/

</style>
