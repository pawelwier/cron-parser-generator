<template>
  <div id="app">
    <TimeInput @time-unit-changed="updateCronPart" v-for="period in timePeriods" :input-title="period" :key="period" />
    <CalendarInput @calendar-unit-changed="updateCronPart" v-for="(unit, i) in calendarUnits" :input-title="unit.name" :units="unit.value" :key="i" />
    <div class="result">
      result: <span>{{finalCronExpression}}</span>
    </div>
  </div>
</template>

<script>
import TimeInput from './components/TimeInput.vue'
import CalendarInput from './components/CalendarInput.vue'

export default {
  name: 'App',
  components: {
    TimeInput,
    CalendarInput
  },
  data() {
    return {
      timePeriods: ['Second', 'Minute', 'Hour'],
      weekDays: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
      months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
      cronParts: ['Second', 'Minute', 'Hour', 'Day of the month', 'Month', 'Day of the week'].map(
        part => {
          return {
            unit: part,
            value: '*'
          }
        }
      ),

    }
  },
  computed: {
    finalCronExpression() {
      return this.cronParts.map(part => part.value).join(' ')
    },
    monthDays() {
      const days = []
      let index = 1
      while (index <= 31) {
        days.push(index)
        index++
      }
      return days
    },
    calendarUnits() {
      return [
        {name: 'Day of the month', value: this.monthDays},
        {name: 'Month', value: this.months},
        {name: 'Day of the week', value: this.weekDays},
      ]
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
