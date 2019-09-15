<template>
  <li>
      {{beer.name}}
      <button v-on:click="removeFavourite">Remove Favourite</button>
  </li>
</template>

<script>

  import {eventBus} from '../main'

export default {
  props:["beer"],
  methods: {
      removeFavourite: function(){
          eventBus.$emit("favourite-removed", this.beer)
      }
  }
}
</script>

<style>
li{ list-style-type: none; }

button{
    background-color:gray;
    border: none;
    color:honeydew;
    border-radius: 8px;
    transition: all 0.5s
}
</style>