<template>
  <div id="app">
    <h1>To do list</h1>
    <hr>
    <router-view />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import AddTodo from "./components/AddTodo.vue"

export default {
  name: "app",
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => {
          this.todos = json
        })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(function (t) {
        return t.id !== id;
      });
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList,
    AddTodo
  },
};
</script>

<style scoped>

</style>