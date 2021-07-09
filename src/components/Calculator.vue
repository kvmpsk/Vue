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

    <input type="checkbox" id="display" @click="keybuttonVisible = !keybuttonVisible">
    <label for="display" >Отобразить экранную клавиатуру</label>

    <div class="keybutton" v-if="keybuttonVisible">
      <div>
        <button v-for="(item, idx) in calcButton" :key="idx">
          {{ item }}
        </button>
      </div>

      <div class="check_operand">
        <label for="operand1">
          <input type="radio" id="operand1"><span>Операнд1</span>
        </label>

        <label for="operand2">
          <input type="radio" id="operand2"><span>Операнд2</span>
        </label>
      </div>
    </div>
  </div>


</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      keybuttonVisible: true,
      operand1: 0,
      operand2: 0,
      result: 0,
      error: "",
      logs: {},
      calcButton: [0,1,2,3,4,5,6,7,8,9,'<' ],
      operands: ['+', '-', '/', '*']
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
  margin-bottom: 10px;
}
.keyboard {
  margin-top: 20px;
  margin-bottom: 10px;
}
</style>