<template>
  <main>
    <h1 v-if="filmFromApp.length < 0 && tvFromApp.length < 0">Inizia la tua ricerca di film e serie tv</h1>
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
 background: rgb(10,10,10);
background: linear-gradient(0deg, rgba(10,10,10,1) 2%, rgba(62,62,62,1) 21%, rgba(62,62,62,1) 59%, rgba(9,9,9,1) 75%, rgba(0,0,0,1) 100%);
  min-height: 100vh;
  padding-top: 100px;
  min-width: 6500px;
}
</style>