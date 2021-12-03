<template>
  <div class="box m-2 p-1">
    <div class="flip-card ">
      <div class="flip-card-inner ">
        <div class="flip-card-front">
          <img :src="cardImage" alt="">
        </div>
        <div class="flip-card-back d-flex flex-column justify-content-center align-items-center">
          <h2>{{title}}</h2>
          <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
          <div><strong>Lingua originale:</strong> 
            <img v-if="flags.includes(language)" class="img-language ps-2" :src="require(`../assets/img/${language}.png`)" alt="">
            <span v-else>{{language}}</span>
          </div> 
          <p><strong>Voto:</strong>{{vote}}</p> 
          <div class="description container">
            <strong>Descrizione:</strong>
            <p v-if="description != ''">{{description}}</p>
            <p v-else>Non disponibile</p>
          </div>
        </div>
      </div>
    </div>


    
  </div>
</template>

<script>
export default {
  name: 'Card',
  props:{
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    image: String,
    description: String
  },
  data(){
    return{
      cardImage : '',
      flags:['it', 'en'],
    }
  },
  methods:{
    poster(){
      if(this.image != undefined){
        this.cardImage = `https://image.tmdb.org/t/p/w342${this.image}`;
        
      }else{
        this.cardImage = `https://via.placeholder.com/342x515/000000/FFFFFF/?text=${this.title}`;
      }
    }
  },
  mounted(){
    this.poster()
  }
}
</script>

<style lang="scss" scope>
@import '../assets/style/vars.scss';
.box{
    min-width: 200px;
    cursor: pointer;
    .img-language{
      width: 25px;
    }
    h2{
      text-transform: uppercase;
      cursor: pointer;
      &hover{
        color: darken($color: $brand-color, $amount: 10%);
      }
  
    }
    .description{
      overflow-y: scroll;
      scrollbar-color: white grey;
      scrollbar-width: thin;
      height: 250px;
    }
    
    .flip-card {
      width: 345px;
      height: 515px;
      perspective: 1000px;
    }
    .flip-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      text-align: center;
      transition: transform 1.5s;
      transform-style: preserve-3d;
    }
    .flip-card:hover .flip-card-inner {
      transform: rotateY(180deg);
    }
    .flip-card-front, .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      -webkit-backface-visibility: hidden; /* Safari */
      backface-visibility: hidden;
    }
    .flip-card-back {
      background-color: grey;
      color: white;
      transform: rotateY(180deg);
    }
  }
</style>