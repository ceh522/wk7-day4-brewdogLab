<template lang="html">
  <div>
    <h1>Brewdog API</h1>
    <beer-filter-form :beers="beers" />
    <beer-detail />
  </div>
</template>

<script>
import BeerFilterForm from './components/BeerFilterForm.vue'
import BeerDetail from './components/BeerDetail.vue'

export default {
  data(){
    return {
      beers: [],
    }
  },
  components: {
    "beer-filter-form": BeerFilterForm,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)
  }
}
</script>

<style lang="css" scoped>
h1 {
  text-align: center;
  color: #333;
}
</style>
