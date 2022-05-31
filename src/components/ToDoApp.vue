<template>
  <div class="to-do-app-block">
    <to-do-form @add-to-do="addToDo"/>
    <ul class="to-do-list" v-if="toDoArr && toDoArr.length">
      <to-do-item v-for="todo in toDoArr"
                  :todo="todo"
                  :key="todo.id"
                  @delete-to-do="deleteToDo"
                  @edit-to-do="editToDo"/>
    </ul>
    <p class="empty-list" v-else>Nothing to do</p>
    <button @click="deleteAll"
            :disabled="!toDoArr.length"
            class="clear-all-button">
      Clear All
    </button>
  </div>
</template>

<script>
import ToDoForm from "@/components/ToDoForm";
import ToDoItem from "@/components/ToDoItem";

export default {
  name: 'ToDoApp',
  components: {ToDoItem, ToDoForm},
  data() {
    return {
      toDoArr: []
    }
  },
  methods: {
    addToDo(todo) {
      const newToDo = {
        id: Number(new Date()),
        content: todo,
        isCompleted: false,
      }
      this.toDoArr.push(newToDo)
      console.log(newToDo)
    },
    deleteToDo(id) {
      const index = this.toDoArr.findIndex(item => item.id === id)
      this.toDoArr.splice(index, 1)
    },
    editToDo(id) {
      const index = this.toDoArr.findIndex(item => item.id === id)
      this.toDoArr[index] = {...this.toDoArr[index], isCompleted: !this.toDoArr[index].isCompleted}
    },
    deleteAll() {
      this.toDoArr = []
    }
  }
}
</script>

<style scoped>
  .to-do-app-block {
    display: flex;
    flex-direction: column;
    margin: auto;
    background-color: #fff;
    width: 100%;
    max-width: 500px;
    min-width: 300px;
    min-height: 500px;
    box-shadow: 0px 0px 24px 10px rgba(49,62,132,0.33);
    padding-bottom: 16px;
  }

  .to-do-list {
    padding: 12px 24px;
    text-align: left;
    flex-grow: 1;
  }
  .empty-list {
    padding: 12px;
    font-size: 20px;
    flex-grow: 1;
  }
  .clear-all-button {
    align-self: center;
    padding: 8px;
    width: 120px;
    background-color: #3c1362;
    border: none;
    color: #ffffff;
    box-shadow: 0px 0px 24px 10px rgba(95, 49, 132, 0.33);
    cursor: pointer;
  }
  .clear-all-button[disabled] {
    background-color: #4f2573;
    color: #aa8fc4;
  }

</style>
