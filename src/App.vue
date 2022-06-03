<template>
  <div id="app">
    <mapa-component></mapa-component>
  </div>
</template>

<script>
import MapaComponent from "./components/MapaComponent.vue";

export default {
  name: "App",
  components: {
    MapaComponent,
  },
};
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
</style>
