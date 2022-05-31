<template>
  <li class="todo-item">
    <span class="todo-text" :class="{done: todo.isCompleted}" @click="$emit('editToDo', todo.id)">{{ todo.content }} </span>
    <button class="delete-todo-button" @click="$emit('deleteToDo', todo.id)">✖</button>
  </li>
</template>

<script>
export default {
  name: 'ToDoItem',
  props: {
    todo: Object,
  }
}
</script>

<style scoped>
.todo-text {
  cursor: pointer;
  text-decoration: none;
}
.done {
  text-decoration: line-through;
}
.todo-item {
  border-bottom: 2px solid #c9bede;
  display: flex;
  justify-content: space-between;
  padding: 4px 12px 0 12px;
  margin-bottom: 12px;
}
.delete-todo-button {
  background-color: transparent;
  color: #be1414;
  border: none;
  cursor: pointer;
}


</style>
