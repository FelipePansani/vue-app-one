<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos.vue";
import Header from "../components/Header.vue";
import AddTodo from "../components/AddTodo.vue";

import axios from "axios";

export default {
  name: "Home",
  components: {
    Header,
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          (res) => (this.todos = this.todos.filter((todo) => todo.id !== id))
        )
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { id, title, completed } = newTodo;

      console.log(newTodo);
      axios
        .post("http://jsonplaceholder.typicode.com/users/1/todos", {
          id,
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("http://jsonplaceholder.typicode.com/users/1/todos?_limit=2")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* color: #2c3e50; */
  margin: 0px;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  padding: 7px 20px;
  cursor: pointer;
  color: #fff;
}

.btn:hover {
  background: #666;
}
</style>
