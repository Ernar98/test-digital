<template>
  <div class="container p-5">
    <MainFilter  />
    <MainTodos v-bind:data="todos" />
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
    async getTodos() {
      let request = await this.$axios.$get(
        "https://jsonplaceholder.typicode.com/todos?_limit=20"
      );
      this.todos = request;
    },
    showAlert(){
      alert("AWFAWF")
    }
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
