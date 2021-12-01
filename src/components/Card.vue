<template>
  <div>
    <h4>{{objectFromMain.title}}</h4>
    <h4>{{objectFromMain.original_title}}</h4>
    <h4>{{objectFromMain.original_language}}</h4>
    <h4>{{objectFromMain.original_vote_average}}</h4>
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
