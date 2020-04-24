<template>
  <div id="app">
    <Anchor></Anchor>
  </div>
</template>

<script>
import Anchor from './components/anchor'

export default {
  name: 'App',
  components: {
    Anchor
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
