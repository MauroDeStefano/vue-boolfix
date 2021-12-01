<template>
  <header>
    <div class="search-and-logo d-flex justify-content-between align-items-center">
      <div class="logo">Logo</div>
      <div class="d-flex justify-content-around">
        <input v-model="searchText" placeholder="Cerca" type="text" @keyup.enter="$emit('textToApp', searchText)">
        <button @click="$emit('textToApp', searchText)" >CERCA</button>
        
        <select name="" id="">
          <option>Film</option>
          <option>Serie TV</option>
        </select> 
        
      </div>  
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      searchText : "",
    }
  },
  // methods:{
  //   refresh(){
  //     vm.$forceUpdate();
  //   }
  // }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
header{
  background-color: black;
  width: 100%;
  height: 100px;
}

.logo{
  font-size: 35px;
  color: red;
}

.search-and-logo{
  height: 100%;
  padding: 10px;
  input, select, button{
    margin: 0 10px;
  }
}
</style>
