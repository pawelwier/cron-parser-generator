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
        <input type="text">
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
        <input type="text">
      </div>
    </div>
    <div class="input-wrapper" @click="setMethod(3)">
      <div>
        Every {{ unit }} between
      </div>
      <div>
        <input type="text">
      </div>
      <div>
        and
      </div>
      <div>
        <input type="text">
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
    }
  },
  computed:{
    unit() {
      return this.inputTitle.toLowerCase()
    },
    result() {
      return 'x'
    },
  },
  methods: {
    setMethod(param) {
      console.log(param)
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
