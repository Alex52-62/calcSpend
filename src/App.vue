<template>
  <div id="app" :class="[$style.wrapper]">
    <header>
      <h1>My personal cost</h1>
    </header>
    <main>
      <PaymentsDisplay :list="paymentsList" />
      <br />
      <AddPayment @addNewPayment="addData" />
      <br />
      <Pagination :pd="paymentsList" />
    </main>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
import AddPayment from "./components/AddPayment.vue";
import Pagination from "./components/pagination.vue";

export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPayment,
    Pagination,
  },
  data: () => ({
    paymentsList: [],
    data: {
      form: "qw",
    },
  }),
  methods: {
    addData(data) {
      console.log("push to state", data);
      // this.paymentsList.push(data)
      this.paymentsList = [...this.paymentsList, data];
      console.log(this.paymentsList);
    },
    fetchData() {
      return [
        {
          date: "28.03.2020",
          category: "Food",
          value: 169,
        },
        {
          date: "20.04.2021",
          category: "Sport",
          value: 400,
        },
        {
          date: "28.05.2020",
          category: "Internet",
          value: 200,
        },
        {
          date: "28.05.2020",
          category: "Internet",
          value: 210,
        },
        {
          date: "28.05.2020",
          category: "Internet",
          value: 220,
        },
        {
          date: "28.05.2020",
          category: "Internet",
          value: 250,
        },
      ];
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss" module>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
