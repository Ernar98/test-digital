<template>
  <div class="container p-5">
    <MainFilter :onFilter="setFilter" />
    <MainTodos :data="todos" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
    };
  },

  created: function () {
    this.getTodos();
  },

  methods: {
    async setFilter(id) {
      let request = await this.$axios.$get(
        "https://jsonplaceholder.typicode.com/todos?userId=" + id
      );
      this.todos = request;
    },

    async getTodos() {
      let request = await this.$axios.$get(
        "https://jsonplaceholder.typicode.com/todos?_limit=20"
      );
      this.todos = request;
    },
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
</style>
