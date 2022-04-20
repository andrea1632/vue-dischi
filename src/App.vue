<template>
  <div>

  </div>
</template>

<script>

import axios from 'axios';
import "bootstrap"
export default {
  name: 'App',
  components: {

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


</style>
