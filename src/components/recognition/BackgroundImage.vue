<template>
  <div class="bg-image"></div>
</template>

<script>
export default {};
</script>

<style scoped>
.bg-image {
  background-image: url("../../assets/bg.jpg");
  position: fixed;
  top: 0;
  z-index: -1;
  background-size: cover;
  height: 100vh;
  width: 100vw;
  background-repeat: no-repeat;
  background-position: center center;
}
.bg-image::after {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100vw;
  background: #08171a;
  opacity: 0.8;
  filter: contrast(0.85);
  z-index: 1;
}
</style>
