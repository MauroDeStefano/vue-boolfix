<template>
  <div>
    <Card 
    v-for="film in films"
    :key="film.id"
    :objectFromMain="films" />
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "Main",
  
  components:{
    Card,
  },

 
  data(){
    return{
      films : [],
      loaded : false,
      selection : "movie",
      titleSelected: "ritorno al futuro"
    }
  },

  methods:{
    getApi(){
      axios.get(`https://api.themoviedb.org/3/search/${this.selection}`,{  
        
        params:{
          api_key : "2090ddf1b621c402cd194562f23c0ea3",
          query : this.titleSelected,
          language: "it-IT"
        }
      }).then( r => {
        this.films = r.data.results;
        this.loaded = true;
        console.log(this.films);
      }).catch(e => {
        console.log(e);
      });
    }},
    mounted(){
      this.getApi();
    }
  }
</script>

<style lang="scss">

</style>