<template class='template' lang="html">
  <div class="app">

  <weather-controllers class='controllers':weatherData='this.weatherData'
  :weatherLocation='this.weatherLocation'>
  </weather-controllers>

  <map-controllers class='controllers' v-if='this.weatherLocation.lat && this.weatherLocation.lon'
  :weatherData='this.weatherData'
  :weatherLocation='this.weatherLocation'>
  </map-controllers>

</div>

</template>

<script>
import {eventBus} from '@/main.js'
import {keys} from './keys.js';
import weatherControllers from '@/components/weatherControllers.vue'
import mapControllers from '@/components/mapControls.vue'


export default {
  name: 'app',
  data() {
    return {
      weatherData: null,
      weatherLocation: {lat: null, lon: null}
    }
  },
  mounted() {
    let lat;
    let lon;
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(position => {
        lat = position.coords.latitude;
        lon = position.coords.longitude;
        this.setCoods(lat, lon);
        this.apiCall(lat, lon);
      })
    }

    console.log(this.weatherLocation);
  },
  components: {
    'weather-controllers': weatherControllers,
    'map-controllers': mapControllers

  },
  methods: {
    apiCall(lat, lon) {
      console.log("Api Called")
      fetch(`http://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&units=metric&APPID=${keys.weatherKey}`)
        .then(res => res.json())
        .then(data => this.weatherData = data)
      },
      setCoods(lat, lon) {
        this.weatherLocation = {lat: lat, lon: lon}
      }
    }
  }
</script>

<style lang="css" scoped>

  * {
    color: #F2EFED
  }

  .app {
    background-image: linear-gradient(#1D76C4, #6BC1E0);
  }

</style>
