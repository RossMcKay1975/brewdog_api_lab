<template lang="html">
  <div v-if="beer" id="beerDetail">
    <div id="detailWrapper">
    <h2>{{ beer.name }}</h2>
    <div id="flexWrapper">
    </div>
      <div id="left">
        <p><span>Strength</span>: {{beer.abv}}</p>
        <p><span>Paired Food</span>:</p>
          <ul v-for="food in beer.food_pairing">
              <li>{{ food }}</li>
          </ul>
        <p><span>This beer is a favourite</span>: </p>

      </div>
      <div id="right">
        <button type="button" v-on:click="makeFavourite">Make Favourite</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    makeFavourite: function(){
      this.beer.favourite = true
    }
  }
}
</script>

<style lang="css" scoped>

  ul {
    list-style-type: none;
    }

  .button {
    background-color: #4CAF50;
  }



</style>
