<template>
  <header>
    <div class="search-and-logo d-flex justify-content-between align-items-center">
      <div class="logo">BOOLFLIX</div>
      <div class="d-flex justify-content-around">
        <input class="" v-model="searchText" placeholder="Cerca" type="text" @keyup.enter="sendEmit()">
        <button class="btn btn-danger" @click="sendEmit()">CERCA</button>
      
        
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
  methods:{
    sendEmit(){
      this.$emit('textToApp', this.searchText);
      this.searchText = "";
    }
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
header{
  background-color: black;
  width: 100%;
  height: 100px;
  position: fixed;
  z-index: 999;
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
