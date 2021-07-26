<template>
  <div>
    <h2>
      {{inputTitle}}
    </h2>
    <div v-for="(unit, i) in unitsMapped" :key="i">
      <input type="checkbox" :id="unit.name" v-model="unit.checked" @change="unitsEdited">
      <label>{{unit.name}}</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalendarInput",
  props: {
    inputTitle: {
      type: String,
      required: true,
    },
    units: {
      type: Array,
      required: true,
    }
  },
  data() {
    return {
      unitValue: {
        type: String,
        value: '',
      }
    }
  },
  methods: {
    unitsEdited() {
      this.unitValue = this.unitsMapped.filter(unit => unit.checked).map(unit => unit.value).join(',')
      this.$emit('calendar-unit-changed', {
        name: this.inputTitle,
        value: this.unitValue,
      })
    }
  },
  computed: {
    unitsMapped() {
      return this.units.map((unit, i) => {
        return {
          value: i + 1,
          name: unit,
          checked: false,
        }
      })
    },
  }
}
</script>

<style scoped>

</style>
