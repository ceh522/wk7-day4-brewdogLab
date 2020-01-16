<template lang='html'>
  <div v-if="beer" id="beerDetail">
    <div id="detailWrapper">
      <h2>{{beer.name}}</h2>
      <div id="flexwrapper">
        <div id="left">
          <p><span></span> {{beer.tagline}}</p>
          <p><span>Description</span>: {{beer.description}}</p>
          <!-- <p><span>Ingredients:</span></p>
          <p><span>Malt:</span></p>
          <ul v-for="ingredient in beer.ingredients">
            <li>{{ingredient.malt}}</li>
          </ul> -->

          <p><span>Food Pairing</span>: {{beer.food_pairing[0]}}</p>
          <p><span>Brewer's Tips</span>: {{beer.brewers_tips}}</p>
        </div>

        <div id="right">
          <img :src="beer.image_url" :alt="beer.name">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beer-detail',
  data(){
    return {
      beer: null
    }
  },
  mounted(){
    eventBus.$on('beer-selected', (beer) => {
      this.beer = beer
    })
  }
}
</script>

<style lang="css" scoped>


#detailWrapper {
  box-sizing: border-box;
  background: #fff;
  padding: 10px;
  height: 100%;
  border-radius: 3px;
}

#flexWrapper {
  display: flex;
  justify-content: space-between;
}

#left, #right {
  width: 45%;
}

#right img {
  width: 100%;
}

#left p:first-child {
  margin-top: 0;
}

h2 {
  margin: 10px 0 20px;
  padding: 0;
}

p span {
  font-weight: bold;
}

</style>
