<template>
<div>
  <Header @textToApp="getEmit" />
  <Main :objectFromApp="films"/>
</div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data(){
    return{
      films : [],
      loaded : false,
      selection : "movie",
      titleSelected: this.textFromApp,
    }
  },

  methods:{
    getEmit(text){
      axios.get(`https://api.themoviedb.org/3/search/${this.selection}`,{  
        
        params:{
          api_key : "2090ddf1b621c402cd194562f23c0ea3",
          query : text,
          language: "it-IT"
        }

      }).then( r => {
        this.films = r.data.results;
        this.loaded = true;
        console.log(this.films);
      }).catch(e => {
        console.log(e);
      }); 
    },

  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
</style>
