<template>
  <div>
    <Card 
    v-for="film in objectFromApp"
    :key="film.id"
    :objectFromMain="film" />
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
    objectFromApp: Array,
  },

  }
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
</style>