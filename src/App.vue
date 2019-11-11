<template>
  <div id="app">
    <animation-container/>
  </div>
</template>

<script>
import 'bulma/css/bulma.css'
import AnimationContainer from './components/AnimationContainer.vue'

export default {
  name: 'app',
  components: {
    AnimationContainer
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
