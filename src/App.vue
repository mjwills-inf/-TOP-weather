<template>
  <div id="app">
    <LocationInput v-on:new-call="callApi" />    
    <Output v-bind:weatherData="weatherData" />
  </div>
</template>

<script>
import LocationInput from './components/LocationInput';
import Output from './components/Output';


export default {
  name: 'App',
  components: {
    LocationInput,    
    Output
  },
  data() {
    return {      
      openWeatherUrl: "http://api.openweathermap.org/data/2.5/weather?q=",
      searchTerm: "",
      unit: "",
      openWeatherKey: "&appid=dcd2e6326d2fb8503d3cfb017aef3301",
      weatherData: {}
    }
  },
  computed: {
    targetUrl() {
      return `${this.openWeatherUrl}${this.searchTerm}&units=${this.unit}${this.openWeatherKey}`
    }
  }, 
  methods: {
    callApi(payload) {

      this.searchTerm = payload.search
      this.unit = payload.unit
      
      fetch(this.targetUrl)
        .then(fetchResponse => fetchResponse.json())
        .then(jsonResponse => this.buildWeatherData(jsonResponse))
        .catch(anyReject => {
          console.log("inside of catch")
          console.log(anyReject)
        });     
    },
    buildWeatherData(apiData) {
      if (apiData.cod == 200) {
        this.weatherData = { ...apiData }
        console.log(this.weatherData)
      }

        // YARRRRRR
    }
  }
}
</script>

<style>

@import url("./assets/css/reset.css");

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
  min-width: 360px;
  height: 100vh;
  background: linear-gradient(#00449e, #536070, #be7f92, #e66465); 
}
</style>
