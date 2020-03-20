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
      places: [
        {
          lat: 37.974728,
          long: -122.03711,
          description: "Alpine Bakery in Concord, delicious pastries!"
        },
        {
          lat: 36.973804,
          long: -122.02575,
          description: "Marinis is my favorite ice cream in Santa Cruz"
        },
        {
          lat: 37.791852,
          long: -122.42127,
          description: "Bob's Donuts in SF makes gigantic donuts, good for sharing (or eating alone!)"
        }
      ]
    };
  },
  created: function() {
    // do mapbox after axios promise to ensure data from the backend exists before trying to geocode address

    // axios.get("/api/events/1").then(response => {
    //   this.event = response.data;
    //   mapboxgl.accessToken = '<your access token>';
    //   var mapboxClient = mapboxSdk({ accessToken: mapboxgl.accessToken });
    //   mapboxClient.geocoding
    //     .forwardGeocode({
    //       query: this.event.address,
    //       autocomplete: false,
    //       limit: 1
    //     })
    //     .send()
    //     .then(function(response) {
    //       if (
    //         response &&
    //         response.body &&
    //         response.body.features &&
    //         response.body.features.length
    //       ) {
    //         var feature = response.body.features[0];
           
    //         var map = new mapboxgl.Map({
    //           container: 'map',
    //           style: 'mapbox://styles/mapbox/streets-v11',
    //           center: feature.center,
    //           zoom: 10
    //         });
    //         new mapboxgl.Marker().setLngLat(feature.center).addTo(map);
    //       }
    //     });
    // })
  },
  mounted: function() {
    // basic example with hardcoded string of geocoding
    mapboxgl.accessToken = 'pk.eyJ1IjoiZHphZ2hpYW4iLCJhIjoiY2pzbnF0NmV0MGY2czQzbXBpMjcwMzRmNiJ9.Jei4-17Vu7hJSerisjPCEg';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/dzaghian/cjxaqxm273umk1cqz0saddk4t', // stylesheet location
        center: [-122.4194, 37.7749], // starting position [lng, lat]
        zoom: 7 // starting zoom
    });
    this.places.forEach(place => {
      var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
      var marker = new mapboxgl.Marker()
        .setLngLat([place.long, place.lat])
        .setPopup(popup)
        .addTo(map);
    });
    // var mapboxClient = mapboxSdk({ accessToken: mapboxgl.accessToken });
    // mapboxClient.geocoding
    //   .forwardGeocode({
    //     query: '520 8th Avenute, NY',
    //     autocomplete: false,
    //     limit: 1
    //   })
    //   .send()
    //   .then(function(response) {
    //     if (
    //       response &&
    //       response.body &&
    //       response.body.features &&
    //       response.body.features.length
    //     ) {
    //       var feature = response.body.features[0];
         
    //       var map = new mapboxgl.Map({
    //         container: 'map',
    //         style: 'mapbox://styles/mapbox/streets-v11',
    //         center: feature.center,
    //         zoom: 10
    //       });
    //       new mapboxgl.Marker().setLngLat(feature.center).addTo(map);
    //     }
    //   });
  },
  methods: {}
};
</script>
