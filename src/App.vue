<template>
  <div id="app" :class="[$style.wrapper]">
    <header>
      <h1>My personal cost</h1>
    </header>
    <main>
      <PaymentsDisplay :list="pageList" />
      <br />
      <AddPayment @addNewPayment="addData" />
      <br />
      <Pagination :pd="paymentsList" @sendPage="getPage($event)" />
    </main>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
import AddPayment from "./components/AddPayment.vue";
import Pagination from "./components/pagination.vue";
import list from "@/data";

export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPayment,
    Pagination,
  },
  data: () => ({
    paymentsList: [],
    pageList: [],
    data: {
      form: "qw",
    },
  }),
  methods: {
    getPage(page) {
      this.pageList = page;
    },
    addData(data) {
      this.paymentsList = [...this.paymentsList, data];
    },
  },
  created() {
    this.paymentsList = list();
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
