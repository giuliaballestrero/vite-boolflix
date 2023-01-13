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
    }
  },

  methods: {
    getMovies () {
      console.log();
      axios.get('', {
        params: {
          
        }
      })


      .then(() => {
        console.log();
        
    })   
    }
  },

  created() {
    this.getMovies();
  },
}

</script>

<template>

  <HeaderApp/>
  
  <MainApp />

</template>

<style lang="scss">

@use './styles/general.scss' as *;
@use './styles/partials/_variables.scss' as *;

</style>
