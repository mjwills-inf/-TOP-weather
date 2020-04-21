<template>
  <div class="container">
    <div class="banner">
      <div class="filler"></div>
      <div class="filler"></div>
      <img src="../assets/img/logo.png" class="vue-logo" alt="vue-logo" width="40px" />
      <div class="filler"></div>
      <div class="filler"></div>
    </div>
    
    <div class="entry">      
    
      <div class="entry-left">
        <input v-model="locationTextInput" class="location-text" name="location-text" type="text" placeholder="City:">      
        <button v-on:click="formatInput" class="location-button">Get Weather</button>
      </div>
      
      <div class="temp">
        <p>Temp:</p>
        <div>
          <label class="temp-label" for="fah">&#176;F
            <input type="radio" class="temp-radio" id="fah" value="imperial" name="unit" v-model="tempUnit">
            <span class="checkmark"></span>
          </label>        
        </div>
        <div>
          <label class="temp-label" for="cel">&#176;C
            <input type="radio" class="temp-radio" id ="cel" value="metric" name="unit" v-model="tempUnit" checked>
            <span class="checkmark"></span>
          </label>  
        </div>
      </div>

    </div>
  
  </div>
</template>



<script>
export default {
  name: 'LocationInput',
  data() {
    return {      
      locationTextInput: "",
      tempUnit: "metric"
    }
  },
  methods: {
    formatInput() {
      let formatted = this.locationTextInput      
        .trim()
        .replace(/ /g, "+")
      let unit = this.tempUnit      
      this.$emit("new-call", {search: formatted, unit: unit})
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

.banner {
  display: flex;  
  align-content: center;
  justify-content: space-evenly;
  margin: 15px;
}

.filler {
  display: inline-block;
  width: 40px;
  height: 40px;
  border: 1px solid gray;
  margin: 2px;
}

.vue-logo {
  display: inline-block;
  height: 40px;
  width: 40px;
  border: 1px solid gray;
  margin: 2px;
}

.entry {
  margin: 10px 10px 5px;
  display: grid;
  grid-template-columns: 4fr 1fr;
}

.location-text {
  outline: none;
  border: none;  
  box-shadow: none;
  margin-bottom: 10px;  
  padding: 10px;
  width: 220px;
  height: 30px;
  font-size: 15px;  
  background: rgb(210, 210, 210);
  border-bottom: 2px solid rgb(150, 150, 150);  
}

.location-text:hover {
  border-bottom: 2px solid #00449e;
}

.location-button {
  display: block;
  margin: 10px auto 0px;
  padding: 5px;
  width: 220px; 
  border-radius: 5px;
  border: 1.5px solid #00449e;
  color: #00449e;
  font-size: 15px;  
  cursor: pointer;
}

.location-button:hover {
  color: white;
  background-color: #00449e;
}

.temp {
  position: relative;
  left: -5px;
  top: 2px;
  display: flex;
  flex-direction: column;  
  text-align: left;
  justify-content: space-evenly;
  color:rgb(100, 100, 100);
  font-size: 15px;
}

.temp-label {
  display: block;
  position: relative;
  cursor: pointer;
  user-select: none;
  padding-left: 25px;
  margin-top: 3px;
}

.temp-label input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}

.temp-label input:checked ~ .checkmark {
  background-color: #00449e;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 17px;
  width: 17px;
  background-color: rgb(140, 140, 140);
  border-radius: 50%;
}

</style>