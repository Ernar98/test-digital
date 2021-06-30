<template>
  <div class="bg-green-600 p-5 navigation">
    <nuxt-Link to="/" class="title">
      <img src="@/assets/images/to-do-list.svg" />
      <h4 class="text-purple-50 font-extrabold">TEST TO-DO LIST</h4>
    </nuxt-Link>
  </div>
</template>

<script>
export default {
  name: "TheNavigation",
};
</script>

<style>
.navigation {
  display: flex;
  justify-content: center;
  margin: 0 auto;
}

.title {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.title img {
  width: 35px;
  height: 35px;
  margin-right: 15px;
}
</style>