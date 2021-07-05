<template>
  <div class="payments-list">
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>date</th>
          <th>category</th>
          <th>value</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, idx) in list" :key="idx">
          <td>{{ idx + 1 }}</td>
          <td>{{ item.date }}</td>
          <td>{{ item.category }}</td>
          <td>{{ item.value }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    list: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style scoped>
.payments-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid grey;
  width: 60%;
  margin: auto;
}

td {
  border-bottom: 1px solid grey;
}

th {
  padding: 10px;
}
</style>