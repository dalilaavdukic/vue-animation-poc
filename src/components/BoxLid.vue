<template>
  <div class="image-container" :style="{ top: -(height/2) + 'px', left: -(width/2) + 'px' }">
    <img src = "images/woodenCrate_02.png"/>
  </div>
</template>

<script>
export default {
  name: 'BoxLid',
    props: {
    width: {
      type: Number,
      default: 300
    },
    height: {
      type: Number,
      default: 300
    }
  },
}
</script>

<style lang="scss" scoped>
.image-container {
  position: absolute;
  img {
    max-width: none;
  }
}
</style>