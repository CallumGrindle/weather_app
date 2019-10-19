<template lang="html">
  <div class="">
    <weather-display class='display-component' v-if='weatherData' :weatherData='this.weatherData'></weather-display>
  </div>
</template>

<script>
import weatherDisplay from '@/components/weatherDisplay.vue'

export default {
  name: 'weather-controllers',
  components: {
    'weather-display': weatherDisplay
  },
  props: ['weatherData']
}
</script>

<style lang="css" scoped>
  .display-component {
    display: flex;
    justify-content: center;
  }
</style>
