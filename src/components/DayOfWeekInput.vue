<template>
  <div>
    <div v-for="(day, i) in days" :key="i">
      <input type="checkbox" :id="day.name" v-model="day.checked">
      <label :for="day.name">{{ day.name }}</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "DayOfWeekInput",
  data() {
    return {
      days: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'].map((day, i) => {
        return {
          value: i,
          name: day,
        }
      }),
    }
  },
}
</script>

<style scoped>

</style>
