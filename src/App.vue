<template>
  <div id="app">
    <h1>Beer App v2.0!</h1>

  </div>
</template>

<script>
import {eventBus} from './main'

export default {
   data(){
     return{
     beers: [],
     selectedBeer: null}
   },
  components: {
    
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
