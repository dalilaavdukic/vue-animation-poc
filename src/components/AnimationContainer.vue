<template>
  <div class="animation-container">
    <background/>
    <box-opening-canvas :boxOpened="boxOpened" :width="canvasWidth" :height="canvasHeight" />
    <transition name="open-fade">
      <box-lid v-if="!boxOpened" :width="canvasWidth+50" :height="canvasHeight+50"/>
    </transition>
    <button v-if="!boxOpened" @click="openBox()" class="button is-primary">Open Box</button>
  </div>
</template>

<script>
import BoxOpeningCanvas from './BoxOpeningCanvas';
import BoxLid from './BoxLid';
import Background from './Background';

export default {
  name: 'AnimationContainer',
  data() {
    return {
      canvasHeight: 250,
      canvasWidth: 250,
      boxOpened: false
    }
  },
  components: {
    BoxOpeningCanvas,
    BoxLid,
    Background
  },
  methods: {
    openBox: function() {
      this.boxOpened = true;
    },
  }
}
</script>

<style lang="scss" scoped>
.animation-container {
  position: relative;
  button {
    position: absolute;
    top: 200px;
    left: -60px;
    background-color: #A3C8E5;
  }
  .open-fade-leave-active {
    transition: transform 3s ease-out, opacity 1.5s ease-out 1.25s;
  }
  .open-fade-leave-to {
    transform: translateY(-350px);
    opacity: 0;
  }
}
</style>
