<template>
  <div>
      <h3>Your favourite beers</h3>
      <favourite-listitem 
      v-for="beer in favourites"
      :beer="beer"
      :key="beer.id"> </favourite-listitem>
  </div>
</template>

<script>
import FavouriteListItem from './FavouriteListItem'

export default {
    props: ["favourites"],
    components:{
        "favourite-listitem": FavouriteListItem
    }
}
</script>

<style>
 .list { display: flex;
  justify-content: flex-end;
  height: 100%;

 }
</style>