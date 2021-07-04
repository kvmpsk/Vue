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
      <button v-for="operand in operands"
              @click="calculate(operand)"
              :key="operand"
              v-bind:title="operand"
              >
            {{ operand }}
      </button>
    </div>


  <div class="keybutton">
      <button v-for="(item, idx) in calcButton" :key="idx">
        {{ item }}
      </button>
  </div>

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
      error: "",
      logs: {},
      calcButton: [0,1,2,3,4,5,6,7,8,9],
      operands: ['+', '-', '/', '*', 'Целочисленное деление']
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
          this.Whole()
          break;
      }
      const key = Date.now()
      this.logs[key] = `${this.operand1}${operation}${this.operand2} = ${this.result}`
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
    Whole() {
      this.result = Math.floor(this.operand1 / this.operand2)
    }
  },
  computed: {

  }
}
</script>

<style scoped>
  .red {
    color: red;
  }
  .keybutton {
    margin-top: 20px;
  }

  .keyboard {
    margin-top: 20px;
    margin-bottom: 5px;
  }
</style>