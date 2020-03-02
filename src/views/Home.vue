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
    mapboxgl.accessToken = 'pk.eyJ1IjoiZHphZ2hpYW4iLCJhIjoiY2pzbnF0NmV0MGY2czQzbXBpMjcwMzRmNiJ9.Jei4-17Vu7hJSerisjPCEg';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
        center: [-122.4194, 37.7749], // starting position [lng, lat]
        zoom: 12 // starting zoom
    });

    var popup = new mapboxgl.Popup({ offset: 25 }).setText(
    'Historic Chinatown, SF'
    );

    var marker = new mapboxgl.Marker()
      .setLngLat([-122.4078, 37.7941])
      .setPopup(popup)
      .addTo(map);
  },
  methods: {}
};
</script>
