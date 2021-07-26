<template>
  <div id="app">
    <TimeInput @time-unit-changed="updateCronPart" v-for="period in timePeriods" :input-title="period" :key="period" />
    <DayOfWeekInput />
    <div class="result">
      result: <span>{{finalCronExpression}}</span>
    </div>
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
  },
  data() {
    return {
      timePeriods: ['Second', 'Minute', 'Hour'],
      cronParts: ['Second', 'Minute', 'Hour', 'MonthDay', 'Month', 'WeekDay'].map(
        part => {
          return {
            unit: part,
            value: '*'
          }
        }
      )
    }
  },
  computed: {
    finalCronExpression() {
      return this.cronParts.map(part => part.value).join(' ')
    }
  },
  methods: {
    updateCronPart(part) {
      this.cronParts = this.cronParts.map(cronPart => {
        if (cronPart.unit !== part.name) return cronPart
        return {
          ...cronPart,
          value: part.value
        }
      })
    },
  },
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

.result {
  padding-top: 20px;
  font-size: 24px;
  font-weight: 700;
}
</style>
