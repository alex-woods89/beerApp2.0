<template>
  <div id="app">
    <h1>Beer App v2.0!</h1>
     <beer-list :beers="beers"></beer-list>
     <beer-detail v-if="selectedBeer" :beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import {eventBus} from './main'
import BeerDetail from './components/BeerDetail'
import BeerList from './components/BeerList'
export default {
   data(){
     return{
     beers: [],
     selectedBeer: null}
   },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on("beer-selected", beer => (this.selectedBeer = beer))
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
