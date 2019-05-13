<template>
  <div id="app">
    <!-- <router-view></router-view> -->
    <TODO>

    </TODO>
  </div>
</template>

<script>
import TODO from './components/to_do.vue'

export default {
  name: 'app',
  components: {
    TODO
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
