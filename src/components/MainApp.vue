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
    <h2>Main</h2>
  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;

</style>
