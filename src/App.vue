<template lang="html">
  <div class="">
    <h1>Country Navigator</h1>
    <div class="container">
      <div class="sidenav">
        <countries-list :countries="countries"></countries-list>
      </div>
      <countries-dropdown :countries="countries"></countries-dropdown>
      <country-detail  :country="selectedCountry"></country-detail>
    </div>

  </div>

</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import CountriesDropdown from './components/CountriesDropdown.vue';
import {eventBus} from './main.js';

export default {
  name: "app",
  data(){
    return {
      countries:[],
      selectedCountry: null
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries=countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "countries-dropdown": CountriesDropdown
  }
}
</script>

<style lang="css" scoped>
template {
  font-family: 'Lato', sans-serif;
}

h1 {
  margin-left: 280px;
  font-family: 'Lato', sans-serif;
}

.container {
  background-color: whitesmoke;
  width: 800px;
  height: 600px;
  padding: 20px;
  margin-left: 280px;
  display: flex;
  justify-content: space-between;
  z-index: 2;
  font-family: 'Lato', sans-serif;
}

.sidenav {
  height: 100%;
  width: 260px;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: steelblue;
  overflow-x: hidden;
  padding-top: 20px;
  color: whitesmoke;
  font-family: 'Lato', sans-serif;
}

</style>
