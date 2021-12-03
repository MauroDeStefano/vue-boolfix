<template>
    <div class="mds-card m-3">
      <div class="flip-card">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <span v-if="objectFromMain.poster_path.length < 0">Immagine copertina di {{objectFromMain.name}}{{objectFromMain.title}}non trovata</span>
            <img v-else class="mds-img-card" :src="'http://image.tmdb.org/t/p/w300' + objectFromMain.poster_path" alt="">
            
          </div>
        <div class="flip-card-back"> 
          <!-- TITOLO -->
          <h4 class="m-4" v-if="objectFromMain.name"><strong>Titolo</strong>: {{objectFromMain.name}}</h4>
          <h4 class="m-4" v-else><strong>Titolo</strong>: {{objectFromMain.title}}</h4>
          <!-- TITOLO ORIGINALE -->
          <h4 v-if="objectFromMain.original_name"><strong>Titolo originale: </strong>{{objectFromMain.original_name}}</h4>
          <h4 v-else><strong>Titolo originale: </strong>{{objectFromMain.original_title}}</h4>
          <!-- LINGUA ORIGINALE -->
          <h4 v-if="objectFromMain.original_language === 'en'"><country-flag country='us' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'it'"><country-flag country='it' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'cn'"><country-flag country='cn' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'ko'"><country-flag country='kr' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'de'"><country-flag country='de' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'fr'"><country-flag country='fr' size='normal'/></h4>
          <h4 v-else-if="objectFromMain.original_language === 'es'"><country-flag country='es' size='normal'/></h4>
          <h4 v-else><strong>Paese d'origine:</strong>{{objectFromMain.original_language}}</h4>
          <!-- STELLE DA UNO A 5 -->
          <h4><strong>voto: </strong><span v-if="objectFromMain.vote_average < 2 && objectFromMain.vote_average >= 0">
            <i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i>
          </span>
            <span v-else-if="objectFromMain.vote_average < 4 && objectFromMain.vote_average >= 2">
            <i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i>
          </span>
          <span v-else-if="objectFromMain.vote_average < 6 && objectFromMain.vote_average >= 4">
            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i>
          </span>
          <span v-else-if="objectFromMain.vote_average < 8 && objectFromMain.vote_average >= 6">
            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
            <i class="fas fa-star"></i><i class="far fa-star"></i>
          </span>
          <span v-else-if="objectFromMain.vote_average <= 10 && objectFromMain.vote_average >= 8">
            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
            <i class="fas fa-star"></i><i class="fas fa-star"></i>
          </span>
          </h4>
          <!-- OVERVIEW -->
          <p class="text-overview p-2"><strong>Overview: </strong>{{objectFromMain.overview}}</p>

          </div>
        </div>
      </div>
    </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {

  name: "Card",
  components:{
    CountryFlag
  },
  props:{
    objectFromMain: Object,
  },
  methods:{
    getNumerVote(num){
      const numRet = Math.floor(num);
      return numRet;
    }
  }

}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.mds-card{
  float: left;
  width: 290px;
  height: 400px;
  
}

.flip-card {
  background-color: transparent;
  width: 290px;
  height: 400px;
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
   overflow: hidden;
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

.fas.fa-star{
  color: yellow;
}

.far.fa-star{
  color: white;
}

.text-overview{
  overflow: auto;
}

.mds-img-card{
  width: 290px;
  height: 400px;
  object-fit: cover;
}

</style>