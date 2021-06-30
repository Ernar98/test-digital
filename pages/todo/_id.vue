<template>
  <div class="todo__container p-9">
    <div v-if="loading">
      <h1 class="text-white">Wait..</h1>
    </div>
    <div v-else>
      <h1 class="text-white">#{{ todoInfo.id }} {{ todoInfo.title }}</h1>
      <div class="details">
        <span class="text-white"
          >The task belongs to user with ID : {{ todoInfo.userId }}</span
        >
        <span class="text-white">Finished status: {{ todoInfo.completed }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: true,
      todoInfo: [],
    };
  },
  created() {
    this.getTodoinfo();
  },
  methods: {
    async getTodoinfo() {
      let request = await this.$axios.$get(
        "https://jsonplaceholder.typicode.com/todos?id=" + this.$route.params.id
      );
      this.todoInfo = request[0];
      this.loading = false;
      console.log(this.todoInfo);
    },
  },
};
</script>

<style>
.todo__container {
  width: 50%;
  margin: 35px auto;
  display: flex;
  flex-direction: column;
  text-align: center;
  border-radius: 5px;
  border: 2px solid #10b981;
}

.todo__container h1 {
  font-size: 35px;
  padding-bottom: 5px;
  border-bottom: 2px solid #10b981;
}

.todo__container span {
  font-size: 18px;
  padding: 5px 0;
  border-bottom: 2px solid #10b981;
  width: 100%;
}

.details {
  display: flex;
  flex-direction: wrap;
  justify-content: space-between;
}

.details span {
  width: 49%;
}
</style>