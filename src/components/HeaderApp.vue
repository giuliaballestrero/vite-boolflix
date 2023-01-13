<script>

export default {

  name: 'HeaderApp',

  data () {
    return {

    }
  }
}

</script>

<template>
  <section class="header-container">
    <h1>Header</h1>
  </section>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/_variables.scss' as *;
.header-container {
  height: 150px;
  background-color: black;
  color: white;

    h1 {
      font-size: 4rem;
    }
}
</style>
