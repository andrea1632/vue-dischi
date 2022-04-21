<template>
  <div>
    <TopLogo @activeGenre="genreSelector"/>
    <div class="bgSpotify">
      <div class="container cardContainer pb-5">
        <div class="row p-5" v-if="cardsArray.length == arrayIndexLength">
          <CardComp
          v-for="(elm, index) in changeList" :key="index"
          :image="elm.poster"
          :title="elm.title"
          :author="elm.author"
          :year="elm.year"
          />
        </div>
        <div v-else class="text-white loader">
          <img src="./assets/img/giphy.gif" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import CardComp from './components/CardComp.vue'
import axios from 'axios';
import TopLogo from './components/TopLogo.vue'
import "bootstrap"
export default {
  name: 'App',
  components: {
    TopLogo,
    CardComp,
  },
    data(){
    return{
      cardsArray: [],
      arrayIndexLength: null,
      selectedGenre: null,
    }
  },
  methods: {
    genreSelector(genre){
      this.selectedGenre = genre
      console.log(this.selectedGenre)
    }
  },
  created(){
    axios.get( 'https://flynn.boolean.careers/exercises/api/array/music' )
    .then ( (res)=>{
      this.cardsArray = res.data.response
      this.arrayIndexLength = res.data.response.length
    } )
    .catch( (error) => {
     console.log( error )
    } )
  },
  computed : {
    changeList(){
      if(this.selectedGenre == "tutti"){
        return this.cardsArray
      }
      return this.cardsArray.filter((item) =>{
        return item.genre
              .toLowerCase()
              .includes(this.selectedGenre)
      })
    }
  }
}
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";
.bgSpotify{
    background-color: #1E2D3B;
}
.loader{
  width: 80%;
  margin: 0 auto;
  height: calc(100vh - 80px);
  img{
    width: 100%;
    margin-top: 100px;
  }
}
</style>
