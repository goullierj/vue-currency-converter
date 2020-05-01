<template>
  <div id="app">
    <img src="../src/assets/money.png" style="width: 25%;">
    <FormCurrency></FormCurrency>
  </div>
</template>

<script>
  import FormCurrency from "./components/FormCurrency.vue"

  export default {
    components: {
      FormCurrency,
    }
  }
</script>