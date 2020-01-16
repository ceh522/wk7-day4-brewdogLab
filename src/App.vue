<template lang="html">
  <div>
  <h1>Brewdog API</h1>
</div>
</template>

<script>
// import

export default {
  data(){
    return {
      beers: [],

  }
},
// components: {
//
// },
mounted(){
  fetch('https://api.punkapi.com/v2/beers')
  .then(res => res.json())
  .then(beers => this.beers = beers)
}
}
</script>

<style> lang="css" scoped>
h1 {
  text-align: center;
  color: #333;

}
</style>
