<template>
  <div class="home">
    <h1>Mortgage Calculator</h1>
    <MortgageCalc msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import MortgageCalc from "@/components/MortgageCalc.vue";

export default {
  name: "home",
  components: {
    MortgageCalc
  }
};
</script>
