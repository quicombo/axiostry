<template>
  <div id="app">    
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <chuck></chuck>
    <imageGet></imageGet>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import chuck from './components/chuck.vue'
import imageGet from './components/imageGet.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    chuck,
    imageGet
  }
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
</style>
