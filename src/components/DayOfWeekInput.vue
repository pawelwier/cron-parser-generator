<template>
  <div>
    <h2>
      Days of the week
    </h2>
    <div @change="daysEdited" v-for="(day, i) in days" :key="i">
      <input type="checkbox" :id="day.name" v-model="day.checked">
      <label :for="day.name">{{ day.name }}</label>
    </div>
    <div>
      {{dayNames}}
    </div>
  </div>
</template>

<script>
export default {
  name: "DayOfWeekInput",
  data() {
    return {
      days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'].map((day, i) => {
        return {
          value: i,
          name: day,
          checked: false,
        }
      }),
    }
  },
  methods: {
    daysEdited() {
      console.log(this.days)
    }
  },
  computed: {
    dayNames() {
      return this.days.filter(day => day.checked).map(day => day.value).join(',')
    }
  }
}
</script>

<style scoped>

</style>
