<template lang="html">
  <div class="details" v-if="country">
    <h3>{{country.name}}</h3>
    <p>{{country.region}}</p>
    <p>{{country.capital}}</p>
    <p>{{country.popular}}</p>
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
  max-width: 200px;
}
</style>
