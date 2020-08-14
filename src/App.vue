<template>
  <div id="app">
    <CombatCounter />
  </div>
</template>

<script>
import CombatCounter from './components/CombatCounter.vue'

export default {
  name: 'App',
  components: {
    CombatCounter
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
