<template lang="html">
  <li v-on:click="handleClick">{{country.name}}</li>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: "country-item",
  props:['country'],
  methods: {
    handleClick(){
      eventBus.$emit('country-selected', this.country);
    }
  }
}
</script>

<style lang="css" scoped>

li {
  list-style: none;
}

</style>
