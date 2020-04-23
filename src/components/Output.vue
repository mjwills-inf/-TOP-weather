<template v-if="this.weatherData">
  <div class="container">
    <div class="location-display">
      <h1>{{ cityName }}</h1>
      <h3>{{ weatherDescription }}</h3>
    </div>
    <div class="info-display">
      <div class="info-left">
        <img src="../assets/img/temperature.png" alt="temp" width="40px">
        <div v-if="this.unit === 'imperial'" >{{ temp }} &#176;F</div>
        <div v-else>{{ temp }} &#176;C</div>
      </div>
      <div class="info-center">
        <img v-bind:src="`http://openweathermap.org/img/wn/${iconID}@2x.png`" alt="weather-icon">
        <h1>{{ weatherName }}</h1>
      </div>
      <div class="info-right">
        <img src="../assets/img/wind.png" alt="temp" width="40px">
        <div v-if="this.unit === 'imperial'" >{{ wind }} mph</div>
        <div v-else>{{ wind }} m/s</div>
      </div>

    </div>
  </div>
</template>




<script>
export default {
  name: 'Output',
  props: ['weatherData', 'unit'],  
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

.location-display {

}

.location-display h1 {
  font-size: 18px;
  margin-bottom: 3px;
}

.location-display h3 {
  font-size: 14px;
  text-transform: capitalize; 
}

.info-display {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr ;
  margin: 10px;
}

.info-left,
.info-right {  
  margin: auto;
}

.info-left img,
.info-right img {  
  margin: 10px;
}


</style>