<template lang="html">
    <div>
        <ul>
            <!-- <beer-item v-for="(beer, index) in beers" :beer="beer" :key="index"></beer-item> -->
            <select v-on:change="handleChange" id="beer-selected" v-model="selectedBeer">
            <option disabled value="">Select a Beer</option>
            <option v-for="(beer, index) in beers" :beer="beer" :value="beer" :key="index">{{beer.name}}</option>
            </select>
        </ul>
    </div>
</template>

<script>
import {eventBus} from '../main.js'
import BeerItem from './BeerItem.vue'
import FavouriteBeers from './FavouriteBeers'
export default {
    name: 'beer-list',
    data(){
        return{
        selectedBeer:null
        }
    },
    props: ['beers'],
    components: {
        "beer-item": BeerItem
    },
    methods: {
        handleChange(){
            eventBus.$emit('beer-selected', this.selectedBeer)
        }
    }
}
</script>

<style>

</style>