<template lang="html">
  <div>
    <h1>All About Beers</h1>
    <div class="main-container">
      <beers-list :beers="beers"></beers-list>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'

export default {
    data(){
      return {
        beers: [],
        selectedBeer: null
      }
    },
    components: {
      "beers-list": BeersList,
      "beer-detail": BeerDetail
    },
    mounted(){
      fetch('https://api.punkapi.com/v2/beers')
      .then(res => res.json())
      .then(beers => {
        for (const beer of beers){
          beer.favourite = false
        }
        this.beers = beers
      })

      eventBus.$on('beer-selected', (beer) => {
        this.selectedBeer = beer
      })
    }
}

</script>



<style>
</style>
