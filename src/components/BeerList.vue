<template>
    <div >
        <h3>All the beers!</h3>
        
            <li>
            <list-component 
            v-for="beer in beers"
            :beer="beer"
            :key="beer.id"
            ></list-component>
            </li>
        
    </div> 
</template>

<script>
  import ListComponent from './ListItem'
export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
      "list-component": ListComponent
  }
}
</script>

<style>
.favlist { display: flex;
  justify-content: flex-start;
  height: 100%;

 }
</style>