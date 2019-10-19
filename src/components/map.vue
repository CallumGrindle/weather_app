<template lang="html">
<div class="mapid">

</div>
</template>

<script>
import {LMap, LTileLayer, LMarker} from 'vue2-leaflet';

export default {
  name: 'map-display',
  data() {
    return {
      mapLocation: {lat: null, lon: null}
    }
  }
  // mounted() {
  // const mymap = L.map('mapid').setView([51.505, -0.09], 13);
  // }
}
</script>

<style lang="css" scoped>
  /* #mapid { height: 180px; } */
</style>
