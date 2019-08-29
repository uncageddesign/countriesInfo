<template lang="html">
  <div class="details" v-if="country">
    <h3>{{country.name}}</h3>
    <p>Region: {{country.region}}</p>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <img :src="country.flag" alt="flag" class="flag">
  </div>
</template>

<script>
export default {
  name: "country-detail",
  props: ['country']
}
</script>

<style lang="css" scoped>

.details {
  width: 400px;
  padding: 10px;
  background-color: lightgrey;
}

.flag {
  max-width: 250px;
}
</style>
