<template lang="html">
  <select v-on:change="handleSelect" v-model="selectedBeer">
    <option disabled value="">Select a beer...</option>
    <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
  </select>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beer-filter-form',
  data(){
    return {
      "selectedBeer": {},
    }
  },
  props: ["beers"],
  methods: {
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
