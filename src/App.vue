<template>
  <div id="app">
    <FormatInput input-title="Second" />
    <FormatInput input-title="Minute" />
    <FormatInput input-title="Hour" />
  </div>
</template>

<script>
import FormatInput from './components/FormatInput.vue'

export default {
  name: 'App',
  components: {
    FormatInput
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}
</style>
