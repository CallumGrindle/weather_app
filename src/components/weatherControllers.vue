<template lang="html">
  <div class="weatherControllers">

    <weather-display class='display-component' v-if='weatherData'
    :weatherData='this.weatherData'></weather-display>
    <weather-search></weather-search>


  </div>
</template>

<script>
import weatherDisplay from '@/components/weatherDisplay.vue'
import weatherSearch from '@/components/weatherSearch.vue'


export default {
  name: 'weather-controllers',
  components: {
    'weather-display': weatherDisplay,
    'weather-search': weatherSearch
  },
  props: ['weatherData', 'weatherLocation']
}
</script>

<style lang="css" scoped>
  .display-component {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 30vh;
    padding-bottom: 20px
  }
  .weatherControllers {
    height: 45vh;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
  }
</style>
