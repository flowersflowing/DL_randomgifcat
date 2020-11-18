<template>
  <div id="app">
    <h1>Random Gif Cat</h1>
    <Formulario/>
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue'

export default {
  name: 'App',
  components: {
    Formulario,
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin: 0;
}
h1 {
  background-color: #a5d9f1;
  padding-top: 2em;
  padding-bottom: 1.5em;
  margin: 0;
}
</style>
