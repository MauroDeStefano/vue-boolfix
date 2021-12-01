<template>
  <div class="row d-flex d-inline-block">
    <h1>Film Trovati</h1>
    <Card 
    v-for="film in filmFromApp"
    :key="film.id"
    :objectFromMain="film" />
    <h1>Serie TV trovate</h1>
    <Card 
    v-for="tv in tvFromApp"
    :key="tv.id"
    :objectFromMain="tv" />
  </div>
</template>

<script>

import Card from "./Card.vue";

export default {
  name: "Main",
  
  components:{
    Card,
  },

  props:{
    filmFromApp: Array,
    tvFromApp: Array
  },

  }
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
</style>