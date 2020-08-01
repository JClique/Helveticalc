<template>
  <div id="app">
    <Header />
    <Calc />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Calc from './components/Calc.vue'

export default {
  name: 'App',
  components: {
    Calc,
    Header
  }
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  font-family: Helvetica, sans-serif;
  text-align: center;

  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
</style>
