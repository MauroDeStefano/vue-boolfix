<template>
    <div class="card col-2">
      <div class="flip-card">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img :src="'http://image.tmdb.org/t/p/w300' + objectFromMain.poster_path" alt="">
          </div>
        <div class="flip-card-back"> 
          <!-- TITOLO -->
          <h4 v-if="objectFromMain.name">titolo {{objectFromMain.name}}</h4>
          <h4 v-else>titolo {{objectFromMain.title}}</h4>
          <!-- TITOLO ORIGINALE -->
          <h4 v-if="objectFromMain.original_name">titolo originale {{objectFromMain.original_name}}</h4>
          <h4 v-else>titolo originale {{objectFromMain.original_title}}</h4>
          <!-- LINGUA ORIGINALE -->
          <h4 v-if="objectFromMain.original_language === 'en'"><country-flag country='us' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'it'"><country-flag country='it' size='normal'/></h4>
          <h4 v-else>paese d'origine: {{objectFromMain.original_language}}</h4>
          <h4>voto {{objectFromMain.vote_average}}</h4>
      
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import CountryFlag from 'vue-country-flag'
export default {

  name: "Card",
  components:{
    CountryFlag
  },
  props:{
    objectFromMain: Object,
  },

}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';



.flip-card {
  background-color: transparent;
  width: 300px;
  height: 450px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;

  img{
    overflow: hidden;
    object-fit: cover;
  }
}

.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  background-color: rgba(0,0,0,0.8);
  color: white;
  transform: rotateY(180deg);
}

</style>