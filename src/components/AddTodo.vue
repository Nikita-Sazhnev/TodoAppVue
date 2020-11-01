<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="todoText" />
    <button type="submit">Add Todo</button>
  </form>
</template>
<script>
export default {
  name: "AddTodo",
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.todoText.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.todoText,
          complete: false,
        };
        this.$emit("add-todo", newTodo);
        this.todoText = "";
      }
    },
  },
};
</script>
<style  scoped>
form {
  display: flex;
  justify-content: center;
}
input {
  width: 20rem;
}
</style>