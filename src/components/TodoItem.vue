<template>
  <li>
    <span :class="{ done: todo.completed }">
      <input @change="completed" type="checkbox" />
      <strong>{{ index + 1 }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button class="rm" @click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      requierd: true,
    },
    index: Number,
  },
  methods: {
    completed: function () {
      this.todo.completed = !this.todo.completed;
    },
  },
  filters: {
    uppercase(val) {
      return val.toUpperCase();
    },
  },
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
}
.rm {
  color: white;
  background: red;
  border-radius: 50%;
}
.done {
  text-decoration: line-through;
}
</style>