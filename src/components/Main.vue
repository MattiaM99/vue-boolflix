<template>
  <main>
    <div class="container">
      <ul class="list">
        <li
        v-for="(film, index) in callMain"
        :key="index"
        >
          <h2>{{film.original_title}}</h2>
          <h3>{{film.title}}</h3>
          <h5>{{film.original_language}}</h5>
          <p>{{film.original_vote_average}}</p>
        </li>
      </ul>
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
    callMain: String
  },
  
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
  }
}
</style>