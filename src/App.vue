<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App" :date="currentDate"/>
    <button v-on:click="onclick">Click me </button> / {{ count }}
    <button @:click="count = 1 + 2">Sum</button>
    <button @:click="onclick2(1, 4)">Click me 2</button>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      count: 0,
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
