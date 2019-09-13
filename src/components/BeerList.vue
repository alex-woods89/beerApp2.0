<template>
    <select v-on:change="handleChange" v-model="selectedBeer">
        <option v-for="(beer, index) in beers" :value="beer">{{beer.name}}</option>
    </select>    
</template>

<script>
export default {

}
</script>

<style>

</style>