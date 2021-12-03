<template>
  <div id="app">
    <Header @sendSearch="getFilm"
    @sendType="foundType"/>
    <Main 
    v-if="films.length !== 0 || series.length !== 0"
    :films="films"
    :series="series"
    :type="type"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      films: [],
      series: [],
      type:'',
      urlMovie: 'https://api.themoviedb.org/3/search/movie',
      urlTv: 'https://api.themoviedb.org/3/search/tv',
      apiAll: {
        api_key: 'e38bdf09ce9b884140ee0902c3248991',
        language: 'it-IT',
        query: ''
      },
      
      loading: false
    }
  },
  methods:{
    getFilm(titolo){
      this.apiAll.query = titolo;
      this.loading = true;
      axios 
        .get(this.urlMovie, {params: this.apiAll})
        .then((response) =>{
          this.films = response.data.results;
          this.loading = false;
          
        })
        .catch((error) =>{
          console.log(error);
        })
      axios
        .get(this.urlTv, {params: this.apiAll})
        .then((response) =>{
          this.series = response.data.results;
          this.loading = false;
        })
        .catch((error) =>{
          console.log(error);
        })
    },
    foundType(tipo){
      this.type = tipo;
      console.log(this.type);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/vars.scss';
</style>