<template lang="html">

    <div v-if="favouriteBeers.length" id="favourite_beers">
      <h2>Favourite Beers</h2>
      <ul>
        <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}} </li>
      </ul>
    </div>
  </template>

  <script>
  import { eventBus } from '../main.js'

  export default {
    name: 'beer-favourite',
    data(){
      return {
        beer: null
      }
    },
    mounted(){
      eventBus.$on('addToFavourites', (beer) => {
        this.favouriteBeers.push(this.selectedBeer)
      })
    }
  }

</script>
