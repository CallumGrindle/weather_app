<template lang="html">
<div class="mapid">
  <h1>hello</h1>
</div>
</template>

<script>
export default {
  name: 'map-display',
  data() {
    return {
      mapLocation: {lat: null, lon: null}
    }
  }
  // mounted() {
  // var mymap = L.map('mapid').setView([51.505, -0.09], 13);
  // }
}
</script>

<style lang="css" scoped>
  /* #mapid { height: 180px; } */
</style>
