<template>
    <div class="mds-card m-3">
      <div class="flip-card">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <span v-if="objectFromMain.poster_path === null">Immagine copertina di {{objectFromMain.name}}{{objectFromMain.title}} non trovata</span>
            <img v-else class="mds-img-card" :src="'http://image.tmdb.org/t/p/w342' + objectFromMain.poster_path" alt="">
            <img class="adult" v-if="objectFromMain.adult === true" :src="require('../assets/img/classification_18+_icon.png')" alt="">
          </div>
        <div class="flip-card-back"> 
          <!-- TITOLO -->
          <h4 class="m-4" v-if="objectFromMain.name"><strong>Titolo</strong>: {{objectFromMain.name}}</h4>
          <h4 class="m-4" v-else><strong>Titolo</strong>: {{objectFromMain.title}}</h4>
          <!-- TITOLO ORIGINALE -->
          <h4 v-if="objectFromMain.original_name"><strong>Titolo originale: </strong>{{objectFromMain.original_name}}</h4>
          <h4 v-else><strong>Titolo originale: </strong>{{objectFromMain.original_title}}</h4>
          <!-- LINGUA ORIGINALE -->
          <h4><country-flag :country="getFlag(objectFromMain.original_language)" size='normal'/></h4>
          
          <!-- STELLE DA UNO A 5 -->
          <h4><strong>voto: </strong>
          <i v-for="(item, index) in 5"
          :key="index"
          class="fa-star"
          :class="index < Math.round(objectFromMain.vote_average/2) ? 'fas' : 'far'">
          </i>
          </h4>
          <!-- OVERVIEW -->
          <p v-if="objectFromMain.overview.length <= 100 && objectFromMain.overview.length > 0 " class="text-overview p-2"><strong>Overview: </strong>{{objectFromMain.overview}}</p>
          <p v-if="objectFromMain.overview.length <= 0" class="text-overview p-2"><strong>Overview non disponibile</strong></p>
          <p v-if="objectFromMain.overview.length > 100" class="text-overview p-2"><strong>Overview: </strong>{{objectFromMain.overview.slice(0,180)}}...</p>
          <a class="btn btn-info btn-pop-up" id="show-modal" @click="showModal = true">info</a>

      <!-- use the modal component, pass in the prop -->
          <Modal v-if="showModal" @close="showModal = false" :objectFromCard="objectFromMain">
        <!--
      you can use custom content here to overwrite
      default content
    -->
          <h5 slot="header">{{objectFromMain.title || objectFromMain.name}}</h5>
          <p slot="body">Data prouzione: {{objectFromMain.release_date || objectFromMain.first_air_date}}</p>
          <p slot="body"></p>
          <p slot="body">{{objectFromMain.overview}}</p>
           </Modal>
          </div>


          </div>
        </div>
      </div>
</template>

<script>
import Modal from "./Modal.vue";
import CountryFlag from 'vue-country-flag';

export default {

  name: "Card",
  components:{
    CountryFlag,
    Modal
  },
  data(){
    return{
      showModal: false,
      flag :"",
    }
  },
  props:{
    objectFromMain: Object,
  },
  methods:{
    getNumerVote(num){
      const numRet = Math.floor(num);
      return numRet;
    },
    getFlag(flag){
      let flagOut =""
      if(flag === "en"){
        flagOut = "us";
      }else{
        flagOut = this.objectFromMain.original_language;
      }
      return flagOut;
    }
  }

}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.mds-card{
  float: left;
  width: 330px;
  height: 440px;
  
}

.flip-card {
  background-color: transparent;
  width: 330px;
  height: 440px;
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
  width: 330px;
  height: 440px;
  object-fit: cover;
}

.btn-pop-up{
  position:absolute;
  bottom: 0;
  right: 0;
  transform: translate(100% 100%);
  background-color: rgb(190, 9, 9)!important;
  border: solid black !important;
}

.adult{
  position:absolute;
  top:0;
  right: 0;

  img{
    width: 20px;
    height: 20px;
  }  
}


// MODAL///////////////////////////////

</style>