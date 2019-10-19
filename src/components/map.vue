<template lang="html">

<l-map ref="myMap"></l-map>
</template>

<script>
import {LMap, LMarker} from 'vue2-leaflet';
// Vue.component('l-map', Vue2Leaflet.LMap)


export default {
  name: 'map-display',
  data() {
    return {
      mapLocation: null
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
    }
  },
  mounted() {
    if (this.weatherLocation) {
      this.mapLocation = this.weatherLocation
    }
    this.$nextTick(() => {
        this.$refs.myMap.mapObject.ANY_LEAFLET_MAP_METHOD();
      })
  },
  components: {
        LMap,
        LMarker
    },
  props: ['weatherLocation']
}
</script>

<style lang="css" scoped>
  /* #mapid { height: 180px; } */
</style>
