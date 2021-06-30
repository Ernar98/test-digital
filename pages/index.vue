<template>
  <div class="container p-5">
    <TodosFilter @handler-filter="(e) => setFilter(e)" />
    <TodosList :todos="todos" />
  </div>
</template>

<script>
// importy componentov - readablety

import TodosFilter from "~/components/todos/TodosFilter";
import TodosList from "~/components/todos/TodosList";

export default {
  name: "MainPage",
  components: { TodosList, TodosFilter },

  data() {
    return {
      todos: [],
    };
  },

  async fetch() {
    this.todos = await this.$axios.$get(
      "https://jsonplaceholder.typicode.com/todos?_limit=20"
    );
  },

  methods: {
    async setFilter(id) {
      // try catch для обработки ошибок

      // console.error(e) - своя ошибка мб

      const request = await this.$axios.$get(
        "https://jsonplaceholder.typicode.com/todos?userId=" + id
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
