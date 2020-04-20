<template>
  <div class="container">
    <div class="banner">
      <div class="filler">1</div>
      <div class="filler">2</div>
      <img src="../assets/img/logo.png" class="vue-logo" alt="vue-logo" width="40px" />
      <div class="filler">4</div>
      <div class="filler">5</div>
    </div>
    <div class="entry">
      <label for="location">Enter a location</label>
      <br>
      <input id="location" name="location" type="text" placeholder="e.g. Bristol, UK">
      <button>Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LocationInput'  

}
</script>

<style scoped>
.container {
  margin: 10px auto;
  max-width: 500px;
  border: 1px solid black;
}

.banner {
  display: flex;
  align-content: center;
  justify-content: center;
  margin: 10px;
}

.filler {
  display: inline-block;
  width: 40px;
  height: 40px;
  border: 1px solid blue;
  margin: 2px;
}

.vue-logo {
  display: inline-block;
  height: 40px;
  width: 40px;
  border: 1px solid blue;
  margin: 2px;
}

.entry {
  margin: 10px;
}

</style>