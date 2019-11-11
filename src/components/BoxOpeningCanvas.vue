<template>
  <div class="canvas-container" :style="{ top: -(height/2) + 'px', left: -(width/2) + 'px' }">
    <canvas ref="boxOpeningAnimation"></canvas>
  </div>
</template>

<script>
import sprite from '../helpers/sprite';

const BOX_OPENING_IMAGE_PATH = 'images/boxOpening_sprite_complete_03.png';

export default {
  name: 'BoxOpeningCanvas',
  props: {
    boxOpened: {
      type: Boolean,
      default: false
    },
    width: {
      type: Number,
      default: 300
    },
    height: {
      type: Number,
      default: 300
    }
  },
  data() {
    return {
      canvas: {},
      boxImage: new Image(),
      boxSprite: {}
    }
  },
  methods: {
    getCanvas: function() {
      this.canvas = this.$refs.boxOpeningAnimation;
      this.canvas.width = this.width;
      this.canvas.height = this.height;
    },
    animate: function() {
      requestAnimationFrame(this.animate);

      this.boxSprite.update();
      this.boxSprite.render();
    }
  },
  mounted() {
    this.getCanvas();
    this.boxImage.src = BOX_OPENING_IMAGE_PATH;

    this.boxSprite = sprite({
      context: this.canvas.getContext("2d"),
      width: this.width*4,
      height: this.height,
      image: this.boxImage,
      numberOfFrames: 4,
      ticksPerFrame: 20,
      loop: false
    });

    this.boxImage.onload = () => {
      this.boxSprite.render();
    }
  },
  watch: {
    boxOpened: function(boxOpenedNew) {
      if(boxOpenedNew) {
        setTimeout(() => {
          this.animate();
        }, 800); 
      }
    }
  },
}
</script>

<style lang="scss" scoped>
.canvas-container {
  position: absolute;
}
</style>