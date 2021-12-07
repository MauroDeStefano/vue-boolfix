<template>
  <main>
    <div v-if="filmFromApp.length <= 0 && tvFromApp.length <= 0"><h1 class="text-white text-center m-5">SCRIVI QUALE FILM O SERIE TV VUOI CERCARE</h1></div>

    <div v-else class="mds-container" >

      <div class="mds-row">
        <h1 class="p-4 text-white" v-if="filmFromApp.length > 0" >Film Trovati</h1>
        <div v-if="filmFromApp.length >= 5" class="icons-carousel icons-carousel-left" @click="showPrev"></div>
     
        <VueSlickCarousel v-bind="settings" ref="carousel">
          <Card
          v-for="film in filmFromApp"
          :key="film.id"
          :objectFromMain="film" />
        </VueSlickCarousel>

        <div v-if="filmFromApp.length >= 5" class="icons-carousel icons-carousel-right" @click="showNext"></div>
      </div>

      <div class="mds-row">
        <h1 class="p-4 text-white" v-if="tvFromApp.length > 0">Serie TV trovate</h1>
          <div v-if="tvFromApp.length >= 5" class="icons-carousel icons-carousel-left" @click="showPrev2"></div>

            <VueSlickCarousel v-bind="settings" ref="carousel2" >  
              <Card 
              v-for="tv in tvFromApp"
              :key="tv.id"
              :objectFromMain="tv" />
            </VueSlickCarousel>
     
          <div v-if="tvFromApp.length >= 5" class="icons-carousel icons-carousel-right" @click="showNext2"></div>
        </div>

    </div>
  </main>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';
import Card from "./Card.vue";

export default {
  name: "Main",
  
  components:{
    Card,
    VueSlickCarousel
  },

  props:{
    filmFromApp: Array,
    tvFromApp: Array
  },
  
  methods: {
      showNext() {
        this.$refs.carousel.next();
      },
      showPrev(){
        this.$refs.carousel.prev();
      },
      showNext2() {
        this.$refs.carousel2.next();
      },
      showPrev2(){
        this.$refs.carousel2.prev();
      },

  },

  data(){
    return{
      settings:{
        "dots": false,
        "focusOnSelect": false,
        "infinite": true,
        "speed": 400,
        "slidesToShow": 4,
        "slidesToScroll": 1,
        "touchThreshold": 0,
        "variableWidth": true,
        "variableHeight": true,
        "loop":true,
        "centerMode": true,
            
      }
    }
  }
  }
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import '~@fortawesome/fontawesome-free/css/all.min.css';
main{
  background: rgb(60,60,60);
  background: linear-gradient(90deg, rgba(60,60,60,1) 30%, rgba(34,34,34,1) 50%, rgba(60,60,60,1) 70%);
  min-height: 100vh;
  
  padding-top: 100px;
}

.mds-container{
  max-width: 1800px;
  margin: 0 auto;
}

.mds-row{
  position: relative;
}

.icons-carousel{
  height: 441px;
  width: 360px;
  position: absolute;
  top: 120px;
background: rgb(0, 0, 0);


  z-index: 998;

  i{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 30px;
    color: white;
  }
}

.icons-carousel-left{
background: linear-gradient(270deg, rgba(0,0,0,0) 1%, rgba(19,19,19,0.5998774509803921) 19%, rgba(11,11,11,0.8127626050420168) 54%, rgba(60,60,60,1) 76%);
  left: 0;
}

.icons-carousel-right{

background: linear-gradient(90deg, rgba(0,0,0,0) 1%, rgba(19,19,19,0.5998774509803921) 19%, rgba(11,11,11,0.8127626050420168) 54%, rgba(60,60,60,1) 76%);
  right: 0;
}

</style>