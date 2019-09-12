<template lang="html">
  <li v-on:click="handleClick" v-bind:class="{'favourited': beer.favourite}">{{beer.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'list-component',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer)
    }
  }
}
</script>


<style lang="css" scoped>

  .favourited {
    color: red;
  }
</style>

export default {
  name: 'list-component',
