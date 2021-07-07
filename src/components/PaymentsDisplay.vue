<template>
  <div :class="[$style.wrapper]">
    <header>
      <div :class="[$style.title]">My personal costs</div>
    </header>
    <main>
      <PaymentsDisplay/>
    </main>
  </div>
</template>

<script>

export default {
  props: ['items'],
}
</script>

<style scoped>

</style>