<template>
  <div>
    <TopLogo/>
    <div class="bgSpotify">
      <div class="container cardContainer pb-5">
        <div class="row p-5">
          <CardComp
          v-for="(elm, index) in cardsArray" :key="index"
          :image="elm.poster"
          :title="elm.title"
          :author="elm.author"
          :year="elm.year"
          />
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
      cardsArray: []
    }
  },
  created(){
    axios.get( 'https://flynn.boolean.careers/exercises/api/array/music' )
    .then ( (res)=>{
      this.cardsArray = res.data.response
    } )
    .catch( (error) => {
     console.log( error )
    } )
  }
}
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";
.bgSpotify{
    background-color: #1E2D3B;
}
</style>
