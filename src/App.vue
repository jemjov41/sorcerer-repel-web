<template>
  <div id="app">
    <Villager/>
  </div>
</template>

<script>
import Villager from './components/VilagerCalculate.vue'

export default {
  name: 'App',
  components: {
    Villager
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
}
</style>
