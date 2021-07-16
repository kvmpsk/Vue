<template>
  <div class="payments-list">
    <div class="list">
      <div class="item"
           v-for="(item, idx) in items"
           :key="idx">
        {{ item.id }} - {{ item }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    items: {
      type: Array,
      default: ()=>[],
    }
  }
}
</script>