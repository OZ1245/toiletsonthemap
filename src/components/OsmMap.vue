<template>
  <div class="map-container flex">
    <l-map
      ref="map"
      v-model:zoom="zoom"
      :center="center"
      class="map"
    >
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        layer-type="base"
        name="OpenStreetMap"
      ></l-tile-layer>
    </l-map>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { LMap, LTileLayer } from "@vue-leaflet/vue-leaflet";
import "leaflet/dist/leaflet.css";

export default defineComponent({
  name: 'OsmMap',

  components: {
    LMap,
    LTileLayer,
  },

  data() {
    return {
      zoom: 2,
      center: [47.41322, -1.219482]
    };
  },
});
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
