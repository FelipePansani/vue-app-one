<template>
  <header class="header">
    <h1>TodoList</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["header"],
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
}
</style>