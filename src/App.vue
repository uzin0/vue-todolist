<template>
  <div id="app">
    <screen-component/>
  </div>
</template>

<script>
import Screen from './components/Screen'

export default {
  name: 'App',
  components: {
    'screen-component':Screen
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
