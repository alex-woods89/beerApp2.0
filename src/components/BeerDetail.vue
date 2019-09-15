<template>
      <article v-if="beer">  
     <h3>{{beer.name}}</h3>
     <div>
         <p>ABV: {{beer.abv}}%</p>
         <img :src="beer.image_url"  height="300">
         <p>{{beer.description}}</p>  
         <p>{{beer.brewers_tips}}</p>
         <button v-on:click="addFavourite">Mark as favourite</button>      
     </div>
    </article>
</template>

<script>
import { eventBus } from '../main'

export default {
  name: 'beer-detail',
  props:['beer'],
  methods:{
    addFavourite: function() {
        eventBus.$emit("favourite-added", this.beer)
    }
}
}

</script>

<style>

</style>