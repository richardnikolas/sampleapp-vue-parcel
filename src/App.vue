<template>
  <div id="app">
    <Villains />
  </div>
</template>

<script>
import Villains from './components/VillainsPage.vue'

export default {
  name: 'App',
  components: {
    Villains
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #011e2c;
  height: 100%;
}
</style>
