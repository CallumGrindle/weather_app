<template lang="html">
  <div class="weatherControllers">

    <weather-display class='display-component' v-if='weatherData'
    :weatherData='this.weatherData'></weather-display>

    <map-display v-if='this.weatherLocation.lat && this.weatherLocation.lon'
    :weatherData='this.weatherData'
    :weatherLocation='this.weatherLocation'>
    </map-display>
  </div>
</template>

<script>
import weatherDisplay from '@/components/weatherDisplay.vue'
import mapComponent from '@/components/map.vue'

export default {
  name: 'weather-controllers',
  components: {
    'weather-display': weatherDisplay,
    'map-display': mapComponent
  },
  props: ['weatherData', 'weatherLocation']
}
</script>

<style lang="css" scoped>
  .display-component {
    display: flex;
    justify-content: center;
  }
  .weatherControllers {
    height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
  }
</style>
