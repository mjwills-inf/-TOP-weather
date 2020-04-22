<template>
  <div class="container">
    Hello Output
  </div>
</template>




<script>
export default {
  name: 'Output',
  props: ['weatherData'],  
  computed: {
    cityName: function() {
      return this.weatherData.name
    },
    weatherName: function() {
      return this.weatherData.weather[0].main
    },
    weatherDescription: function() {
      return this.weatherData.weather[0].description
    },
    iconID: function() {
      return this.weatherData.weather[0].icon
    },
    temp: function() {
      return this.weatherData.main.temp
    },
    wind: function() {
      return this.weatherData.wind.speed
    }    
  }
}
</script>




<style scoped>
.container {
  margin: 10px auto;
  padding: 10px;
  max-width: 400px;
  border-radius: 10px;
  background-color: rgb(210, 210, 210);
}
</style>