<template>
    <div class="card ">
      <!-- TITOLO -->
      <h4 v-if="objectFromMain.name">titolo {{objectFromMain.name}}</h4>
      <h4 v-else>titolo {{objectFromMain.title}}</h4>
      <!-- TITOLO ORIGINALE -->
      <h4 v-if="objectFromMain.original_name">titolo originale {{objectFromMain.original_name}}</h4>
      <h4 v-else>titolo originale {{objectFromMain.original_title}}</h4>
      <!-- LINGUA ORIGINALE -->
      <h4 v-if="objectFromMain.original_language === 'en'"><country-flag country='us' size='normal'/></h4>
      <h4 v-else-if="objectFromMain.original_language === 'it'"><country-flag country='it' size='normal'/></h4>
      <h4 v-else>paese d'origine{{objectFromMain.original_language}}</h4>
      <h4>voto {{objectFromMain.vote_average}}</h4>

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

.card{
  width: 150px;
  height: 300px;
  background-color: aquamarine;
}

</style>