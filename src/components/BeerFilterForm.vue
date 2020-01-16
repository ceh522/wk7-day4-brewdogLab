<template lang="html">
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="Search for beer:" v-on:keyup="searchForBeer">
    <select v-on:change="handleSelect" v-model="selectedBeer">
      <option disabled value="">Select a beer...</option>
      <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
    </select>
  </form>
</template>

    <script>
    import { eventBus } from '../main.js'

    export default {
      name: 'beer-filter-form',
      data(){
        return {
          "search": "",
          "selectedBeer": {},
        }
      },
      props: ["beers"],
      methods: {
        searchForBeer(){
          let foundBeer = this.beers.find((beer) => {
            return beer.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
          })
          this.selectedBeer = foundBeer

          eventBus.$emit('beer-selected', this.selectedBeer)
        },
        handleSelect(){
          this.search = ""
          eventBus.$emit('beer-selected', this.selectedBeer)
        }
      }
    }
    </script>

    <style lang="css" scoped>
    form{
      text-align: center;
      margin: 40px 0;
    }

    select, input[type="text"]{
      font-size: 18px;
    }

    select {
      margin-left: 20px;
    }
    </style>
