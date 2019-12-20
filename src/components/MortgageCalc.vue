<template>
  <div class="mortgage-calc">
    <div class="row justify-content-center">
      <div class="col-4 input-group mb-3" align="center">
        <div class="input-group-prepend">
          <span class="input-group-text">Amount</span>
        </div>
        <input
          type="text"
          v-model="amount"
          class="form-control"
          aria-label="Dollar amount (with dot and two decimal places)"
        />
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-4 input-group">
        <div class="input-group-prepend">
          <span class="input-group-text">Interest Rate</span>
        </div>
        <input
          type="text"
          v-model="interestRate"
          class="form-control"
          aria-label="Dollar amount (with dot and two decimal places)"
        />
      </div>
    </div>
    <div class="row mt-3 justify-content-center">
      <div class="col-4 form-group">
        <label for>Term</label>
        <select class="form-control" v-model="term" name id>
          <option>15</option>
          <option>30</option>
        </select>
      </div>
    </div>
    <button class="btn btn-success mb-3" type="button" @click="calculate()">Calculate</button>
    <div class="col-12">
      <h6>Total Balance = {{this.balance}}</h6>
      <h6>Monthly Payment = {{this.pmt}}</h6>
    </div>
  </div>
</template>


<script>
export default {
  name: "mortgage-calc",
  data() {
    return {
      amount: 0,
      interestRate: 0,
      term: 0,
      balance: 0,
      pmt: 0,
      options: [15, 30]
    };
  },
  computed: {},
  methods: {
    calculate(amount, interest, term) {
      amount = this.amount;
      interest = this.interestRate;
      term = this.term;
      debugger;
      if (!amount || !interest || !term) return { balance: 0, pmt: 0 };

      // Total loan cost in a fixed mortage is:
      // r * p * n / (1 - (1 + r)^-n)

      // where r = interest rate / 12
      // n = number of payments or term * 12
      // p = principal

      const r = (interest * 0.01) / 12;
      const n = term * 12;
      const p = amount;

      this.balance = ((r * p * n) / (1 - Math.pow(1 + r, -n))).toFixed(2);
      this.pmt = (balance / n).toFixed(2);

      // Uncomment for debug output
      // console.log({ amount, interest, term });
      // console.log({ balance, pmt });
    }
  },
  components: {}
};
</script>


<style lang="scss" scoped>
</style>