<template lang="html">
  <div>
    <h1>All About Beers</h1>
    <div class="main-container">
      <beers-list :beers="beers"></beers-list>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue'

export default {
    data(){
      return {
        beers: []
      }
    },
    components: {
      "beers-list": BeersList
    },
    mounted(){
      fetch('https://punkapi.com/documentation/v2')
      .then(res => res.json())
      .then(beers => this.beers = beers)
    }
}

</script>



<style>
</style>
