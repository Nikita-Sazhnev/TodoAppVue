<template>
  <div id="app">
    <h1>Todo</h1>
    <AddTodo @add-todo="addTodo" />
    <select v-model="filterTodo">
      <option value="all">All</option>
      <option value="complited">Completed</option>
      <option value="not-complited">Not complited</option>
    </select>
    <hr />
    <TodoList
      @remove-todo="removeTodo"
      :todos="filteredTodos"
      v-if="filteredTodos.length"
    />
    <p v-else>There are no todos</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Купить хлеб", completed: false },
        { id: 2, title: "Купить дом", completed: false },
        { id: 3, title: "Купить дерево", completed: false },
      ],
      filterTodo: "all",
    };
  },
  components: {
    TodoList,
    AddTodo,
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.unshift(todo);
    },
  },
  computed: {
    filteredTodos() {
      let result;
      switch (this.filterTodo) {
        case "complited":
          result = this.todos.filter((t) => t.completed);
          break;
        case "not-complited":
          result = this.todos.filter((t) => !t.completed);
          break;
        default:
          result = this.todos;
          break;
      }
      return result;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
