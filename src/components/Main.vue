<template>
  <main>
    <div class="container">
      <div class="movies-section">
        <ul class="list">
          <li
          v-for="(film, index) in callMain"
          :key="index"
          >
            <h2>{{film.original_title}}</h2>
            <h3>{{film.title}}</h3>
            <p>{{film.original_vote_average}}</p>
            <p class="language-cont">
              <img
            v-if="checkLanguage(film) !== ''"
              :src="checkLanguage(film)" 
              :alt="film.original_language">
              <span v-else>
                {{ film.original_language }}
              </span>
            </p>
          </li>
        </ul>
      </div>
       <div class="series-section">
         
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  data(){
    return{
      string: ""
    }
  },
  props:{
    callMain: Array
  },
  methods: {
    checkLanguage(content) {
      const language = content.original_language;
      let flag = '';
      console.log('language', this.contents);
      if (language.toLowerCase().includes('it')) return flag = require('../assets/img/it.png');
      if (language.toLowerCase().includes('en')) return flag = require('../assets/img/en.png');
      return flag;
    }
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

main{
  min-height: calc(100vh - 100px);
  background-color: lighten(black, 10%);
  .list{
    display: flex;
    flex-wrap: wrap;
    list-style: none;

    li{
      text-align: center;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      display: flex;
      line-height: 30px;
      margin: 15px;
      background-color: $card-color;
      width: calc(100% / 5);
      padding: 20px;
      height:200px;
      overflow-y: scroll;
      scrollbar-color: black white;
      scrollbar-width: thin;
    }
    .language-cont{
      width: 35px;
      height: 25px;
      background-color:black;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow:5px 4px 7px 3px grey;
      color: white;
    }
    img{
      width: 90%;
    }
  }
}
</style>