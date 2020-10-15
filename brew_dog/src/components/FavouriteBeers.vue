<template>
    <div>
        <h2>Hello</h2>
        <ul>
            <li v-for="(favouriteBeer, index) in favouriteBeers" :favouriteBeer="favouriteBeer" :value="favouriteBeer" :key="index"> {{favouriteBeer.name}} </li>
        </ul>
    </div>
    
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers']

}
</script>

<style>

</style>