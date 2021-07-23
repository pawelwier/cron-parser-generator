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
    <div class="result">
      Result: {{ result }}
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
      result: ''
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
        case 0: this.result = '*'
          break
        case 1: this.result = `*/${this.everyUnit}`
          break
        case 2: this.result = `${this.specificUnit}`
          break
        case 3: this.result = `${this.betweenUnitOne}-${this.betweenUnitTwo}`
          break
      }
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

  .result {
    padding-top: 10px;
  }

  input[type=text] {
    width: 70px;
  }
</style>
