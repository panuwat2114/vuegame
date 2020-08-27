<template>
  <div id="app">
     <player/>
  </div>

</template>

<script>
import player from './components/player'
export default {
  name: 'App',
  components: {
    player
  }
}
</script>

<style>
#app {
  font-family:  'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: red;
  margin-top: 60px;
}
</style>
