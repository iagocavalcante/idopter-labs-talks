<template>
  <div id="app">
    <Random />
  </div>
</template>
<script>
import Random from './components/Random.vue'
export default {
  name: 'App',
  components: {
    Random
  }
}
</script>
<style s>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>