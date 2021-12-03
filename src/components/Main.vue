<template>
  <main class="container-fluid pt-5 ">
    <div 
    v-if="type === 'all' || type === 'films' || type === ''"
    class="film-container">
      <h2>Film:</h2>
      <div class="d-flex justify-content-center flex-wrap">
        <Card  
        v-for="film in films"
        :key="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="film.poster_path"
        :description="film.overview"/>
      </div>
    </div>

    <div 
    v-if="type === 'all' || type === 'series' || type === ''"
    class="serie-container">
      <h2>Serie:</h2>
      <div class="d-flex justify-content-center flex-wrap">
        <Card 
        v-for="serie in series"
        :key="serie.id"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="serie.poster_path"
        :description="serie.overview"/>
      </div>
    </div>
  </main>
</template>

<script>
import Card from './Card.vue'
export default {
  name: 'Main',
  components:{
    Card
  },
  data(){
    return{
     
    }
  },
  props:{
    films: Array,
    series: Array,
    type: String
  },
  methods:{
  }
  
}
</script>

<style lang="scss" scope>
@import '../assets/style/vars.scss';
h2{
  color: $brand-color;
}
  main{
  height: 100%;
  background-image: linear-gradient(to bottom,
    lighten(black, 100%),
    lighten(black, 5%)
  )
  }
</style>