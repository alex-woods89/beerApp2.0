<template>
  <div id="app">
    <h1>Beer App v2.0!</h1>
    <favourites-list :favourites="favourites"></favourites-list>
     <beer-list :beers="beers"></beer-list>
     <beer-detail v-if="selectedBeer" :beer="selectedBeer"></beer-detail>
     
  </div>
</template>

<script>
import {eventBus} from './main'
import BeerDetail from './components/BeerDetail'
import BeerList from './components/BeerList'
import FavouritesList from './components/FavouritesList'

export default {
   data(){
     return{
     beers: [],
     selectedBeer: null,
     favourites: []
     }
   },
   methods: {
     addFavourite: function(beer) {
       const idOfFavourites = (this.favourites.map(favourite => favourite.id))
       if (!this.isBeerAFavourite(beer)) this.favourites.push(beer)
     },
     isBeerAFavourite: function(beer){
       const idOfFavourites = (this.favourites.map(favourite => favourite.id))
       return idOfFavourites.includes(beer.id)
     },
     removeFavourite: function(beer) {
       const index = this.favourites.indexOf(beer)
       this.favourites.splice(index, 1)
     }

   },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourites-list": FavouritesList
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on("beer-selected", beer => (this.selectedBeer = beer));
    eventBus.$on("favourite-added", beer => this.addFavourite(beer));
    eventBus.$on("favourite-removed", beer => this.removeFavourite(beer))
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  background-color: rgba(168, 208, 243, 0.788)
}
</style>
