<template>
  <div id="app">
    <TimeInput input-title="Second" />
    <TimeInput input-title="Minute" />
    <TimeInput input-title="Hour" />
    <DayOfWeekInput />
  </div>
</template>

<script>
import TimeInput from './components/TimeInput.vue'
import DayOfWeekInput from './components/DayOfWeekInput.vue'

export default {
  name: 'App',
  components: {
    TimeInput,
    DayOfWeekInput
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
