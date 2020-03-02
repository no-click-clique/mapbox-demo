<template>
  <div class="home">
    <div id="map"></div>
  </div>
</template>

<style>
  #map { top: 0; bottom: 0; width: 100%; height: 700px; }
</style>

<script>
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!"
    };
  },
  mounted: function() {
    mapboxgl.accessToken = '<your access token>';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
        center: [-87.623177, 41.881832], // starting position [lng, lat]
        zoom: 12 // starting zoom
    });
  },
  methods: {}
};
</script>