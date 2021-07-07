<template>
  <div id="app">
     <HelloWorld/>
    <payments-display :items="paymentsList"/>
    <AddPaymentForm/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PaymentsDisplay from './components/PaymentsDisplay'
import AddPaymentForm from "@/components/AddPaymentForm";
export default {
  name: 'App',
  components: {
    AddPaymentForm,
    HelloWorld,
    PaymentsDisplay,

  },

  data() {
    return {
      paymentsList: [],
    }
  },
  methods: {
    fetchData() {
      return [
        {
          date: '28.03.2020',
          category: 'Food',
          value: 169,
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 360,
        },
        {
          date: '24.03.2020',
          category: 'Food',
          value: 532,
        },
      ]
    },
  },

  created() {
    this.paymentsList = this.fetchData()
  },
}




</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
