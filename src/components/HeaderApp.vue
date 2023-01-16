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
    <h1>Netflix</h1>

    <div class="searchbar">
      <label for="site-search">Search movies:</label>
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
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;

    h1 {
      font-size: 4rem;
      text-align: center;
      padding: 1rem;
      color: red;
      text-transform: uppercase;
    }

    .searchbar {
      padding: 2rem;

        label,
        input,
        button {
          margin-right: 2rem;
        }

        label {
          font-size: 1.5rem;
        }

        input {
          font-size: 1.5rem;
        }

        button {
          padding: 0.5rem 1rem;
          font-size: 1rem;
          font-weight: 600;
          color: white;
          background-color: red;
          border: none;
          border-radius: 5px;
        }
    }
}
</style>
