<template>
  <div>
    <ul>
      <TodoItem
        @remove-todo="removeTodo"
        v-for="(todo, i) in todos"
        :index="i"
        :todo="todo"
        :key="todo.id"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  props: ["todos"],
  components: {
    TodoItem,
  },
  methods: {
    removeTodo: function (id) {
      this.$emit("remove-todo", id);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>