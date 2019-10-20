<template lang="html">

  <div class="map">
    <l-map v-if='this.weatherLocation' :zoom="zoom" :center="center"
    v-on:move='handleMapMove'>
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker :lat-lng="marker"></l-marker>
    </l-map>
  </div>

</template>

<script>
import {LMap,LTileLayer, LMarker} from 'vue2-leaflet';
import {eventBus} from '@/main.js'

export default {
  name: 'map-display',
  data() {
    return {
      mapLocation: null,
      zoom:13,
      center: L.latLng(this.weatherLocation.lat, this.weatherLocation.lon),
      url:'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(this.weatherLocation.lat, this.weatherLocation.lon)
    }
  },
  methods: {
    zoomUpdated (zoom) {
      this.zoom = zoom;
    },
    centerUpdated (center) {
      this.center = center;
    },
    boundsUpdated (bounds) {
      this.bounds = bounds;
    },
    handleMapButtonClick () {
      console.log('clicked');
    },
    handleMapMove () {
      console.log('moved');
    }
  },
  mounted() {
    eventBus.$on('update:center', (location) => {
      console.log(location);

    if (this.weatherLocation.lat && this.weatherLocation.lon)
      {this.mapLocation = this.weatherLocation};
    })
  },
  components: {
        LMap,
        LMarker,
        LTileLayer
    },
  props: ['weatherLocation']
}
</script>

<style lang="css" scoped>
  .map {
    height: 50vh;
    width: 50vh;
  }
</style>
