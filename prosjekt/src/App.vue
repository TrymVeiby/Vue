<template>
  <Page />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <!-- <TestComponent msg="WORLD" /> -->
</template>

<script>
/* eslint-disable */
// import HelloWorld from './components/HelloWorld.vue'
import Page from './components/Page.vue'

export default {
  name: 'App',
  components: {
    Page,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: bisque;
}
h1 {
  color: rgb(255, 255, 255);
  text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000,
    1px 1px 0 #000;
}
</style>
