<template>
    <div>
        <ul>
            <list-component></list-component>
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