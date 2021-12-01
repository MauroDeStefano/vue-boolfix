<template>
<div>
  <Header @textToApp="getEmit" />
  <Main :filmFromApp="films" :tvFromApp="tvSeries" />
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
      tvSeries: [],
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
        
        console.log('films',this.films);
      }).catch(e => {
         console.log(e);
      });
      
      this.selection ="tv"; 

        axios.get(`https://api.themoviedb.org/3/search/${this.selection}`,{  
        
        params:{
          api_key : "2090ddf1b621c402cd194562f23c0ea3",
          query : text,
          language: "it-IT"
        }

      }).then( r => {
        this.tvSeries = r.data.results;
        
        console.log('serie tv',this.tvSeries);
      }).catch(e => {
         console.log(e);
      }); 

      this.selection ="movie";
    },

      //NON PIACE NEANCHE A ME RIPETERMI COSì POI LO SISTEMO.



    // getTvAndMovie(text){
    //   console.log(this.getEmit(text));
    //   this.films = this.getEmit(text);
    //   this.selection = "tv";
    //   console.log(this.films);
    //   this.tvSeries = this.getEmit(text);
    //   this.selection = "movie";
    //   console.log(this.tvSeries);

    // }

  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
</style>
