<template>
  <div class="container">
    {{ errorString }}
  </div>
</template>

<script>
export default {
  name: 'OutputError',
  props: ['code'],
  computed: {
    errorString() {
      if (this.code == 0) {
        return "Unable to reach Weather Data"
      } else if (this.code == 404) {
        return "Unable to find a city that matches your search"
      } else if (this.code == 429) {
        return "To many location searches"
      } else {
        return "Please enter a city name"
      }
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