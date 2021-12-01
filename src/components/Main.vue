<template>
  <div>
    <Card 
    v-for="film in films"
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
    objectFromApp: Object,
  },

  data(){
    return{
      films : this.objectFromApp,
    }
  },

  methods:{
      getFromApp(){
        this.films = this.objectFromApp;
      }
    },
    
    
  }
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
</style>