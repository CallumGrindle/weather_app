<template lang="html">
  <div class="">
    <map-display :weatherData='this.weatherData'></map-display>
    <weather-display class='display-component' v-if='weatherData' :weatherData='this.weatherData'></weather-display>
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
</style>
