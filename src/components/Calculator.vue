<template>
  <div>
    <input type="number" v-model.number="operand1" placeholder="operand1"/>
    <input type="number" v-model.number="operand2" placeholder="operand2"/>
    = {{ result }}


      <div class="keyboard">
        <button @click="result = operand1 + operand2">+</button>
        <button @click="result = operand1 - operand2">-</button>
        <button @click="result = operand1 * operand2">*</button>
        <button @click="result = operand1 / operand2">/</button>

      </div>

    <button @click="powWithOperand">pow</button>
     = {{ powWithOperand }}
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0
    }
  },
  methods: {

  },
  computed: {
    powWithOperand() {
      return Math.pow(this.operand1, this.operand2)
    }
  }
}
</script>

<style scoped>

</style>