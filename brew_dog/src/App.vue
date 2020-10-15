<template lang='html'>
  <div id="app">
    <h1>A Comprehensive List of Brewdogs Beers</h1>
    <div>
    <beer-list :beers='beers'></beer-list>
    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavouriteBeer"> Add to Favourites List</button>
    <button v-if="favouriteBeers.includes(selectedBeer)" v-on:click="removeFromFavourites"> Remove From Favourites List</button>
    <beer-details :beer="selectedBeer"></beer-details>
    <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import BeerList from './components/BeerList.vue'
import BeerDetails from './components/BeerDetails.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'
// import BeerIngrediants from './components/BeerIngrediants.vue'

export default {
  name: 'App',
  data(){
    return{
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    }
  },
  mounted(){
      fetch('https://api.punkapi.com/v2/beers')
      .then(res => res.json())
      .then(beers => this.beers = beers)

      eventBus.$on('beer-selected', (beer) => {
        this.selectedBeer = beer
      })
  },
  components: {
    'beer-list': BeerList,
    'beer-details': BeerDetails,
    'favourite-beers': FavouriteBeers

  },
  methods: {
    addToFavouriteBeer(){
      this.favouriteBeers.push(this.selectedBeer)
    },
    removeFromFavourites(){
      this.favouriteBeers.splice(this.selectedBeer[-1], 1)
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
