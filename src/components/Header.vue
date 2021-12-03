<template>
  <header class="d-flex justify-content-between align-items-center">
    <a href="http://localhost:8080/"><h1>BOOLFLIX</h1></a>   
    <div class="input-group mb-3 search-film">
      <input 
      @keyup.enter="searchFilm()"
      v-model="filmToSearch"
      type="text" 
      class="form-control" 
      placeholder="Che film stai cercando?" 
      >
      <button 
      @click="searchFilm()"
      class="btn btn-outline-danger" 
      type="button">Search</button>
    <select 
    v-model="type"
    @change="$emit('sendType', type)"
    class="form-select" 
    aria-label="Default select example">
      <option value="all" selected>All</option>
      <option value="films">Films</option>
      <option value="series">Series</option>
    </select>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      filmToSearch: '',
      type:''
    }
  },
  methods:{
    searchFilm(){
      this.$emit('sendSearch', this.filmToSearch)
      console.log(this.filmToSearch);
    }
  }
}
</script>

<style lang="scss" scope>
@import '../assets/style/vars.scss';
header{
  height: 150px;
  margin: 0 30px;
  a{
    text-decoration: none;
  }
  h1{
    color: $brand-color;
  }
  .search-film{
    width: 30%;
    input{
      width: 250px !important;
      height: 50px;
      flex: none !important;
    }
  } 
  .form-select{
    height: 50px;
  }
}
</style>