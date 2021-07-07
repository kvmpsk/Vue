<template>
  <div :class="[$style.wrapper]">
    <input placeholder="Amount" v-model="amount" />
    <input placeholder="Type" v-model="type" />
    <input placeholder="Date" v-model="date" />
    <button>Save!</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      amount: '',
      type: '',
      date: '',
    }
  }
}



</script>

<style scoped>

</style>