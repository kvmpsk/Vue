<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App" :date="currentDate"/>
    <Calculator/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Calculator from './components/Calculator'


export default {
  name: 'App',
  components: {
    HelloWorld,
    Calculator
  },
  data() {
    return {
      currentDate: new Date().toDateString(),
    }
  },
  methods: {
    onclick() {
      this.count +=1
    },
    onclick2(param1, param2) {
      this.count = param1 + param2
    }
  },
  computed: {

  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
