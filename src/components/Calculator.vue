<template>
  <div>
    <input type="number" v-model.number="operand1" placeholder="operand1"/>
    <input type="number" v-model.number="operand2" placeholder="operand2"/>
    = {{ result }}

    <div class="error"
         :class="{'red': error}">
         {{ error }}
    </div>

      <div class="keyboard">
        <button @click="calculate('+')">+</button>
        <button @click="calculate('-')">-</button>
        <button @click="calculate('*')">*</button>
        <button @click="calculate('/')">/</button>
        <button @click="calculate('Целочисленное деление')">Целочисленное деление</button>


      </div>

      <button @click="powWithOperand">Возведение в степень</button>
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
      result: 0,
      error: ""
    }
  },
  methods: {
    calculate(operation = "+") {
      this.error = "";
      switch (operation) {
        case '+':
          this.add()
          break;
        case '-':
          this.substract()
          break;
        case '*':
          this.multiply()
          break;
        case '/':
          this.divide()
          break;
        case 'Целочисленное деление':
          this.whole()
          break;
      }
    },
    add() {
      this.result = this.operand1 + this.operand2
    },
    substract() {
      this.result = this.operand1 - this.operand2
    },
    multiply() {
      this.result = this.operand1 * this.operand2
    },
    divide() {
      const { operand1, operand2 } = this
      if (operand2 === 0) {
        return this.error = "Делить на 0 нельзя"
      }
      this.result = operand1 / operand2
    },
    whole() {
      this.result = Math.floor(this.operand1 / this.operand2)
    }
  },
  computed: {
    powWithOperand() {
      return Math.pow(this.operand1, this.operand2)
    }
  }
}
</script>

<style scoped>
  .red {
    color: red;
  }
</style>