<template>
  <div id="app">
    <ImageHotspots imageUrl="assets/world.jpg" />
  </div>
</template>

<script>
import ImageHotspots from "./components/ImageHotspots";

export default {
  name: "App",
  components: {
    ImageHotspots,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
