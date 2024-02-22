<template>
  <div class="pagination">
    <button @click="changePage(-1)" :disabled="currentPage === 1"><</button>
    <button v-for="page in totalPages" :key="page" @click="GotoPage(page)" :class="{ active: page === currentPage }">{{ page }}</button>
    <button @click="changePage(1)" :disabled="currentPage === totalPages">></button>
  </div>
</template>

<script>
export default {
  props: {
    currentPage: Number,
    totalPages: Number
  },
  methods: {
    GotoPage(page) {
      this.$emit('page-changed', page);
    },
    changePage(amount) {
      this.$emit('page-changed', this.currentPage + amount);
    }
  }
};
</script>

<style scoped>
.pagination {
  margin-top: 20px;
  margin-bottom: 20px;
  text-align: center;
}

.pagination button {
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 10px;
  border: 1px solid #ccc;
  background-color: #fff;

  box-sizing: border-box;
  /* Gray 4 */
  border: 1px solid rgb(189, 189, 189);
  border-radius: 6px;
  color: rgb(189, 189, 189);

  width: 64px;
  height: 64px;
}

.pagination button.active {
  box-sizing: border-box;
  /* Main color */
  border: 1px solid rgb(24, 91, 195);
  border-radius: 6px;
  /* Main color */
  background: rgb(24, 91, 195);
  color: #fff;
}
</style>