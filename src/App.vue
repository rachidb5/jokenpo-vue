<template>
  <PlayerChoice />
</template>

<script>
import PlayerChoice from './components/PlayerChoice.vue'

export default {
  name: 'App',
  components: {
    PlayerChoice
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
