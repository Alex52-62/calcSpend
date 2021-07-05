<template>
  <div id="pagination" class="container">
    <hr />
    <div class="btn-toolbar">
      <div class="btn-group">
        <button
          class="btn btn-primary"
          v-for="p in pagination.pages"
          @click.prevent="setPage(p)"
          :key="p"
        >
          {{ p }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import _ from "lodash";

export default {
  name: "Pagination",
  props: {
    pd: {
      type: Array,
      default: () => [],
    },
  },
  data: () => ({
    perPage: 5,
    pagination: {},
  }),
  computed: {
    collection() {
      return this.paginate(this.pd);
    },
  },
  methods: {
    setPage(p) {
      this.pagination = this.paginator(this.pd.length, p);
    },
    paginate(pd) {
      return _.slice(
        pd,
        this.pagination.startIndex,
        this.pagination.endIndex + 1
      );
    },
    paginator(totalItems, currentPage) {
      var startIndex = (currentPage - 1) * this.perPage,
        endIndex = Math.min(startIndex + this.perPage - 1, totalItems - 1);

      return {
        currentPage: currentPage,
        startIndex: startIndex,
        endIndex: endIndex,
        pages: _.range(1, Math.ceil(totalItems / this.perPage) + 1),
      };
    },
  },
  created() {
    this.setPage(1);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>