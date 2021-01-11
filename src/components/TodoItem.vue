<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" v-on:change="markComplete">{{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
};
</script>

<style scoped>
.todo-item {
  background: #e7e7e7;
  padding: 10px;
  border-bottom: 1px solid black;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: rgb(238, 79, 79);
  color: white;
  padding: 5px 9px;
  border-radius: 50%;
  border: none;
  float: right;
  cursor: pointer;
}
</style>