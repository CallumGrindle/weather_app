<template lang="html">

<div class="mapid"></div>
</template>

<script>
import {LMap, LMarker} from 'vue2-leaflet';

export default {
  name: 'map-display',
  data() {
    return {
      mapLocation: null
    }
  },
  mounted() {
    if (this.weatherLocation) {
      this.mapLocation = this.weatherLocation
    }
  },
  props: ['weatherLocation']
}
</script>

<style lang="css" scoped>
  /* #mapid { height: 180px; } */
</style>
