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

</style>