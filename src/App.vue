<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/music-note.png" width="200px">
    <Playlist />
  </div>
</template>

<script>
import Playlist from './components/Playlist.vue'

export default {
  name: 'App',
  components: {
    Playlist
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
