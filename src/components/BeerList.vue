<template>
    <div>
        <ul>
            <list-component v-for="(beer, index) in beers" :beer="beer" :key:"index"></list-component>
        </ul>
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

</style>