<template lang="html">

  <article class="map-controllers">

    <button v-on:click='handleMapButtonClick' class='button' type="button" name="button">See Weather Here</button>
    <map-display class='map-display' v-if='this.weatherLocation.lat && this.weatherLocation.lon'
    :weatherData='this.weatherData'
    :weatherLocation='this.weatherLocation'>
    </map-display>

  </article>

</template>

<script>
import mapDisplay from '@/components/map.vue'

export default {
  name:'map-controllers',
  components: {
    'map-display': mapDisplay
  },
  props: ['weatherData', 'weatherLocation']

}
</script>

<style lang="css" scoped>
  .map-controllers {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column
  }
  .map-display {
    padding-top: 10px
  }
</style>
