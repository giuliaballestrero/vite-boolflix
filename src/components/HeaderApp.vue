<script>
import { store } from '../store.js';

export default {

  name: 'HeaderApp',

  data () {
    return {
      store,
    }
  }
}

</script>

<template>
  <section class="header-container">
    <h1>Boolflix</h1>

    <div class="searchbar">
      <label for="site-search">Search the movie:</label>
      <input type="text" id="site-search" v-model="store.searchedText">
      <button @click="$emit('searchedText', store.searchedText)">Search</button>
    </div>

  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;
.header-container {

  background-color: black;
  color: white;

    h1 {
      font-size: 4rem;
      text-align: center;
      padding: 1rem
    }

    .searchbar {
      padding: 2rem;

        label,
        input,
        button {
          font-size: 1.7rem;
          margin-right: 2rem;
        }
    }
}
</style>
