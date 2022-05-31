<template>
  <form class="add-todo-form" @submit.prevent="handleAddToDo">
    <input class="form-input" v-model="currentToDo" placeholder="What do you want to do?">
    <button :disabled="!currentToDo" class="submit-button" type="submit">Add To Do</button>

  </form>
</template>

<script>
export default {
  name: 'ToDoForm',
  data() {
    return {
      currentToDo: '',
    }
  },
  methods: {
    handleAddToDo() {
      this.$emit('addToDo', this.currentToDo);
      this.currentToDo = '';
    }
  }
}
</script>

<style scoped>
.add-todo-form {
  display: flex;
  flex-direction: column;
  gap: 24px;
  padding: 24px;
  align-items: center;
  background: #683394
}
.form-input {
  background-color: transparent;
  border: 0;
  color: #e4ddec;
  width: 60%;
  min-width: 200px;
  text-align: center;
  border-bottom: 1px solid #34146b;
}
.form-input::placeholder {
  color: #4e2772;
  text-align: center;
}

.form-input:active,
.form-input:focus {
  outline:none;
  border-bottom: 1px solid rgb(167, 154, 215);
}

.submit-button {
  padding: 8px;
  max-width: 120px;
  background-color: #3c1362;
  border: none;
  color: #ffffff;
  box-shadow: 0px 0px 24px 10px rgba(95, 49, 132, 0.33);
  cursor: pointer;
}

.submit-button[disabled] {
  background-color: #4f2573;
  color: #7736b4;
}


</style>
