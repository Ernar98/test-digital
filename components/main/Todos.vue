<template>
  <div class="todos_list p-5">
    <h4>TODO LIST</h4>
    <div class="list_body">
      <div class="list_item" v-for="item in this.data" :key="item.id">
        <span>{{ item.id }}.</span>
        <NuxtLink :to="'/todo/' + item.id">{{ item.title }}</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
};
</script>

<style scoped>
.todos_list {
  margin: 25px auto;
  border-radius: 5px;
  border: 2px solid #10b981;
  text-align: center;
  width: 50%;
}

.todos_list h4 {
  color: #10855e;
}

.list_body {
  display: flex;
  flex-direction: column;
}

.list_item {
  display: flex;
  padding: 10px 0;
  border-bottom: 2px solid #10b981;
}

.list_item span {
  color: #10855e;
}

.list_body a {
  color: white;
}
</style>