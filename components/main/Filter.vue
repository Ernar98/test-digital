<template>
  <div class="filter p-5">
    <h3 class="text-white">SORT BY USER :</h3>
    <div class="user-list">
      <div class="user" v-for="user in users" :key="user">
        <span class="text-white">ID:{{ user }}</span>
        <input type="radio" :value="user" v-model="picked" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      picked: 1,
      users: [1, 2, 3, 4, 5, 6, 7, 8, 9],
    };
  },
  watch: {
    picked: function () {
      alert(this.picked);
    },
  },
};
</script>

<style>
.filter {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  width: 80%;
  margin: 0 auto;
  border-radius: 5px;
  border: 2px solid #10b981;
}
.user-list {
  display: flex;
  flex-wrap: wrap;
}

.user {
  margin-left: 15px;
  flex-direction: row-reverse;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  min-width: 50px;
}

input {
  font-size: 14px;
}

input[type="radio"]:after {
  width: 15px;
  height: 15px;
  border-radius: 15px;
  top: -2px;
  left: -1px;
  position: relative;
  content: "";
  display: inline-block;
  visibility: visible;
  background-color: white;
  border: 1px solid #10b981;
}

input[type="radio"]:checked:after {
  width: 15px;
  height: 15px;
  border-radius: 15px;
  top: -2px;
  left: -1px;
  position: relative;
  background-color: black;
  content: "";
  display: inline-block;
  visibility: visible;
  border: 2px solid #10b981;
}
</style>