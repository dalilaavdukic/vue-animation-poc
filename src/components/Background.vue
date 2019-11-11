<template>
  <div class="background-container">
    <div class="diamond-shaped-background"></div>
  </div>
</template>

<script>
export default {
  name: 'BackgroundCanvas',
}
</script>

<style scoped>
@keyframes animatedBackground {
  from {
    background-position: 0 0;
  }
  to {
    background-position: 100% 0;
  }
}
.background-container {
  position: absolute;
  top: -250px;
  left: -250px;
}
.diamond-shaped-background {
  position: relative;
  overflow: hidden;
  height: 500px;
  transform: scaleX(1.6) rotate(45deg);
  width:500px;
}
.diamond-shaped-background:before {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  top: -50%;
  left: -50%;
  z-index: -1;
  background: url('~@/assets/seemlessBackground.jpg') 0 0 repeat;
  background-size: 200px;
  transform: rotate(-45deg);
  animation-name: animatedBackground;
  animation-duration: 50s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}
</style>