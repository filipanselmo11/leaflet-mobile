<template>
  <div id="map"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
export default {
  name: "MapaComponent",
  data: () => ({
    map: undefined,
  }),

  mounted() {
    this.setupMap();
  },

  methods: {
    setupMap() {
      this.map = L.map("map").fitWorld();
      this.map.locate({ setView: true, maxZoom: 16 });
      this.map.on("locationfound", this.onLocationFound);
      this.map.on("locationError", this.onLocationError);
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution: "© OpenStreetMap",
      }).addTo(this.map);
    },
    onLocationFound(e) {
      const radius = e.accuracy;
      // L.marker(e.latlng)
      //   .addTo(this.map)
      //   .bindPopup("You are within " + radius + " meters from this point")
      //   .openPopup();

      L.circle(e.latlng, radius).addTo(this.map);
    },
    onLocationError(e){
        alert(e.message);
    }
  },
};
</script>

<style scoped>

#map {
  height: 100%;
  width: 100vw;
}
</style>
