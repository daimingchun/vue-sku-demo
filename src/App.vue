<template>
  <div id="app">
    <img src="./assets/logo.png">
    <SkuComponent/>
  </div>
</template>

<script>
import SkuComponent from './components/SkuComponent'
export default {
  name: 'app',
  components: {
    SkuComponent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
