<template>
  <header>
    <h1>BOOLFLIX</h1>
    <div>
      <input 
      v-model="searchBar"
      @keyup.enter="search"
      type="text" 
      placeholder="Che film stai cercando?">
      <button
      @click="$emit('search', searchBar)"
      >Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data(){
    return{
      searchBar: ""
    }
  },
  methods:{
    search(){
      this.$emit("search", this.searchBar);
      this.searchBar = "";
    }
  },
  mounted(){
    this.search()
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";
header{
  height: 100px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 25px;
  h1{
    color: $brand-color;
  }
  input{
    font-size: 20px;
    padding: 15px 30px;
  }
  button{
    padding: 10px 15px;
    margin-left: 15px;
    font-size: 15px;
    cursor: pointer;
  }
}
</style>