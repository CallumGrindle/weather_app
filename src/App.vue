<template lang="html">
  <weather-controllers class='controllers':weatherData='this.weatherData'>
  </weather-controllers>
</template>

<script>

import {keys} from './keys.js';
import weatherControllers from '@/components/weatherControllers.vue'

export default {
  name: 'app',
  data() {
    return {
      weatherData: null
    }
  },
  mounted() {
    let lat;
    let lon;
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(position => {
        lat = position.coords.latitude;
        lon = position.coords.longitude;
        this.apiCall(lat, lon);
        console.log("Api Called");
      })
    }
  },
  components: {
    'weather-controllers': weatherControllers
  },
  methods: {
    apiCall(lat, lon) {
      fetch(`http://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&units=metric&APPID=${keys.weatherKey}`)
      .then(res => res.json())
      .then(data => this.weatherData = data)
    }
  }
}
</script>

<style lang="css" scoped>
  .controllers {
    margin: 0;
    padding: 0;
    border: 0;
    box-sizing: border-box;
    background-image: linear-gradient(red, yellow);
    color: #fff
  }


</style>
