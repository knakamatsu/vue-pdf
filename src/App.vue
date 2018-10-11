<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <pdfgen msg="using pdfmake"/>
  </div>
</template>

<script>
import Pdfgen from './components/PDFgen.vue'

export default {
  name: 'app',
  components: {
    Pdfgen
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
