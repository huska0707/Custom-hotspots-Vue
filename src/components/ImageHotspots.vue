<template>
  <div class="image-container" ref="imageContainer">
    <img :src="imageSrc" alt="Hotspot Image" class="image" @click="handleClick($event)" />
    <div
      v-for="(hotspot, index) in hotspots"
      :key="index"
      class="hotspot"
      :style="{ top: hotspot.top, left: hotspot.left }"
      @click="performAction(hotspot.action)"
    >
      <span class="hotspot-marker"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageHotspots",
  data() {
    return {
      imageSrc: require("@/assets/world.jpg"),
      hotspots: [
        { top: "20%", left: "30%", action: "showMessage" },
        { top: "50%", left: "50%", action: "zoomIn" },
        { top: "70%", left: "20%", action: "navigateToView" },
        { top: "80%", left: "60%", action: "showForm" },
        { top: "40%", left: "80%", action: "showAlert" },
      ],
    };
  },
  methods: {
    performAction(action) {
      switch (action) {
        case "showMessage":
          alert("Hello!");
          break;
        case "zoomIn":
          this.zoomImage();
          break;
        case "navigateToView":
          this.$router.push({ name: "AnotherView" });
          break;
        case "showForm":
          // Implement form display logic here
          break;
        case "showAlert":
          alert("You clicked a hotspot!");
          break;
        default:
          console.log("Unknown action");
      }
    },
    zoomImage() {
      this.$refs.imageContainer.style.transform = "scale(1.5)";
      this.$refs.imageContainer.style.transition = "transform 0.3s ease-in-out";
    },
    handleClick(event) {
      console.log("Image clicked at:", event.clientX, event.clientY);
    },
  },
};
</script>

<style scoped>
.image-container {
  position: relative;
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  overflow: hidden;
}
.image {
  width: 100%;
  height: auto;
}
.hotspot {
  position: absolute;
  width: 20px;
  height: 20px;
  background-color: red;
  border-radius: 50%;
  cursor: pointer;
}
.hotspot-marker {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background-color: rgba(255, 0, 0, 0.8);
}
</style>
