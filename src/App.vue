<template>
  <div id="app">
    <LocationInput />
    <Graphic />
    <Output />
  </div>
</template>

<script>
import LocationInput from './components/LocationInput';
import Graphic from './components/Graphic';
import Output from './components/Output'

export default {
  name: 'App',
  components: {
    LocationInput,
    Graphic,
    Output
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
  margin-top: 60px;
  min-width: 360px;
 
}
</style>
