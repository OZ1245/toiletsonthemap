<template>
  <div class="map-container flex">
    <l-map
      ref="map"
      v-model:zoom="zoom"
      :center="center"
      class="map"

      @move="log('move')"
    >
      <l-tile-layer
        :url="url"
        layer-type="base"
        :attribution="attribution"
        name="OpenStreetMap"
      ></l-tile-layer>
    </l-map>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { LMap, LTileLayer } from "@vue-leaflet/vue-leaflet";
import "leaflet/dist/leaflet.css";

const url = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png';
const attribution = '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors';

const zoom = 10;
const center = [47.41322, -1.219482];

onMounted(() => {
  if (navigator.geolocation) {
    // Geolocation available
    const geolocation = navigator.geolocation;

    geolocation.watchPosition((result) => {
      console.log(result)
      center = [result.coords.latitude, result.coords.longitude];
    }, (result) => {
      center = [47.41322, -1.219482];
      throw result;
    });
  }
})
</script>

<style lang="scss" scoped>
.map-container {
  width: 100%;
  height: 100%;
}

.map {
  flex-shrink: 0;
  flex-grow: 1;
  flex-basis: 100%;
}
</style>
