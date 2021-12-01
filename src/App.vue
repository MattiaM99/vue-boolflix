<template>
  <div>
    <Header 
      @search="iniziaRicerca"
    />
    <Main 
      :callMain="search"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios"
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      searchFilm: "",
      search: []
    }
  },
  methods:{
    iniziaRicerca(film){
      this.searchFilm = film;
            axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key: "e38bdf09ce9b884140ee0902c3248991",
          query : this.searchFilm
        }
      })
        .then( r => {
          this.search = r.data.results;
          console.log(r);
        })
        .catch( e => {
          console.log(e);
        });
    }
  }
}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/utilities.scss";
@import "./assets/style/general.scss";
</style>