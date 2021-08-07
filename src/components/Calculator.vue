<template>
  <div>
    <input type="number" v-model.number="operand1" placeholder="operand1"/>
    <input type="number" v-model.number="operand2" placeholder="operand2"/>
    = {{ result }}

      <div class="keyboard">
        <button @click="calculate('+')">+</button>
        <button @click="calculate('-')">-</button>
        <button @click="calculate('*')">*</button>
        <button @click="calculate('/')">/</button>
      </div>

  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    operand1: 0,
    operand2: 0,
    result: 0,
  }),

  methods: {
    calculate(operation) {
      const {operand1, operand2} = this
      const calcOperation = {
        '+': () => operand1 + operand2,
        '-': () => operand1 - operand2,
        '*': () => operand1 * operand2,
        '/': () => operand1 / operand2,
      }
      this.result = calcOperation[operation]()
    },
  }
}


</script>

<style scoped>

</style>