<template>
   <div id="mapContainer">
     <h2> Center is {{currentCenter}}, Zoom id {{currentZoom}} </h2>
     <l-map :zoom="zoom" :center="center" @update:zoom="zoomUpdate" @update:center="centerUpdate">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker
        v-for="(munro, index) in munros" :key="index" 
        :lat-lng="latLng(munro.latlng_lat, munro.latlng_lng)">
      </l-marker>
    </l-map>
   </div>
</template>

<script>
import L from 'leaflet';
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';
import func from '../../vue-temp/vue-editor-bridge';

export default {
  name: 'munro-map',
  props: ['munros'],

  components: {
    LMap,
    LTileLayer,
    LMarker,
  },
  data() {
    return {
      zoom:8,
      center: L.latLng(47.413220, -1.219482),
      currentCenter:  L.latLng(47.413220, -1.219482),
      currnetZoom: 8,
      url:'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(47.413220, -1.219482),
    }
  },
  methods: {
    latLng: function(lat, lng) {
      return L.latLng(lat, lng)
    },
    centerUpdate: function(center){
      this.currentCenter = center
    },
    zoomUpdate: function (zoom){
      this.currnetZoom = zoom
    }
  }
};
</script>

<style scoped>
#mapContainer {
 height: 50vh;
 width: 50vh;
}
</style>
