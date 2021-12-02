<template>
  <main>
    
    <h1 class="p-4 text-white" v-if="filmFromApp.length > 0" >Film Trovati</h1>
    <div class="d-flex d-inline-block">
      <Card 
      v-for="film in filmFromApp"
      :key="film.id"
      :objectFromMain="film" />
    </div>
    <h1 class="p-4 text-white" v-if="tvFromApp.length > 0">Serie TV trovate</h1>
    <div class="d-flex d-inline-block">
      <Card 
      v-for="tv in tvFromApp"
      :key="tv.id"
      :objectFromMain="tv" />
    </div>
  </main>
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

main{
  background-color: rgb(58, 57, 57);
  min-height: calc(100vh - 100px);
}
</style>