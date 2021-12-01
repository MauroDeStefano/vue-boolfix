<template>
  <div>
    <div v-if="objectFromMain !== ''">
      <h4>{{objectFromMain.title}}</h4>
      <h4>{{objectFromMain.original_title}}</h4>
      <h4>{{objectFromMain.original_language}}</h4>
      <h4>{{objectFromMain.original_vote_average}}</h4>
    </div>
    <div v-else>
      <h5>SELEZIONA UN FILM DA CERCARE</h5>
    </div>
  </div>
</template>

<script>

export default {

  name: "Card",

  props:{
    objectFromMain: Object,
  },

}
</script>

<style>

</style>
