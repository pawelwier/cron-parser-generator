<template>
  <div>
   <h2>
    {{ inputTitle }}
   </h2>
    <div class="input-wrapper" @click="setMethod(0)">
      <div>
        Every {{ unit }}
      </div>
    </div>
    <div class="input-wrapper" @click="setMethod(1)">
      <div>
        Every
      </div>
      <div>
        <input type="text" v-model="everyUnit">
      </div>
      <div>
        {{ unit }}(s)
      </div>
    </div>
    <div class="input-wrapper" @click="setMethod(2)">
      <div>
        Specific {{ unit }}(s) (divided by comma ',')
      </div>
      <div>
        <input type="text" v-model="specificUnit">
      </div>
    </div>
    <div class="input-wrapper" @click="setMethod(3)">
      <div>
        Every {{ unit }} between
      </div>
      <div>
        <input type="text" v-model="betweenUnitOne">
      </div>
      <div>
        and
      </div>
      <div>
        <input type="text" v-model="betweenUnitTwo">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormatInput",
  props: {
    inputTitle: {
      required: true,
      type: String,
    }
  },
  data() {
    return {
      everyUnit: '',
      specificUnit: '',
      betweenUnitOne: '',
      betweenUnitTwo: '',
    }
  },
  computed:{
    unit() {
      return this.inputTitle.toLowerCase()
    },
  },
  methods: {
    setMethod(param) {
      switch(param) {
        case 0: this.setResult('*')
          break
        case 1: this.setResult(`*/${this.everyUnit}`)
          break
        case 2: this.setResult(`${this.specificUnit}`)
          break
        case 3: this.setResult(`${this.betweenUnitOne}-${this.betweenUnitTwo}`)
          break
      }
    },
    setResult(val) {
      this.$emit('time-unit-changed', {
        name: this.inputTitle,
        value: val,
      })
    },
  }
}
</script>

<style scoped>
  .input-wrapper {
    display: flex;
    column-gap: 6px;
  }

  .input-wrapper:hover {
    cursor: pointer;
  }

  input[type=text] {
    width: 70px;
  }
</style>
