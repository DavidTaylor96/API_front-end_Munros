<template>
   <div id="mapContainer">
     <!-- <p> Center is {{currentCenter}}, Zoom is {{currentZoom}} </p> -->
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
import { LMap, LTileLayer, LMarker} from 'vue2-leaflet';

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
      zoom:7,
      center: L.latLng(57.292583, -4.848205),
      currentCenter:  L.latLng(57.292583, -4.848205),
      currentZoom: 7,
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
      this.currentZoom = zoom
    }
  }
};
</script>

<style scoped>
#mapContainer {
 margin-top: 10px;
 margin-left: 10px;
 height: 50vh;
 width: 50vh;
}
</style>
