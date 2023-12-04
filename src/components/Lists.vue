<template>
  <li class="list" v-for="(todo, index) in todos" :key="index">
    <span v-if="!todo.isEditing" @dblclick="editTodo(index, )">{{ todo.text }}</span>
    
    <input
      autofocus
      type="text"
      v-if="todo.isEditing"
      v-model="todo.editedText"
      @keyup.enter="updateTodo(index)"
    />
    &nbsp;
    
    <div class="btn-container">
      <RemoveButton class="action-btn" @removeTodo="removeTodo(index)" :todos="this.todos" :todo="this.todo" v-if="!todo.isEditing"></RemoveButton>
      <EditButton class="action-btn" @editTodo="editTodo(index)" v-if="!todo.isEditing"></EditButton>
      <UpdateButton class="action-btn" @handleUpdate="handleUpdate(index)" v-if="todo.isEditing"></UpdateButton>
    </div>
  </li>
</template>

<script>
import RemoveButton from "./RemoveButton.vue";
import UpdateButton from "./UpdateButton.vue";
import EditButton from "./EditButton.vue";

export default {
  name: "Lists",

  methods: {
    removeTodo(index) {
      let confirmDelete = confirm("You are about to delete this item");
      if (confirmDelete) {
        this.todos.splice(index, 1);
      }
    },

    editTodo(index) {
      this.todos[index].isEditing = true;
      this.todos[index].editedText = this.todos[index].text;
    },

    updateTodo(index) {
      if (this.todos[index].editedText) {
        this.todos[index].text = this.todos[index].editedText;
        this.todos[index].isEditing = false;
        this.todos[index].editedText = "";
      } else {
        alert("Please enter an item");
      }
    },

    handleUpdate(index) {
      this.updateTodo(index);
    },
  },

  components: {
    RemoveButton,
    UpdateButton,
    EditButton,
  },

  props: {
    todos: Array,
    todo: String,
  }
};
</script>

<style scoped>
  .list {
    list-style-type: none;

    display: flex;
    justify-content: space-between;

    background-color: hsl(0, 0%, 20%, .2);
    padding: .5em 1em;
    border-radius: .5rem;
  }

  .btn-container {
    display: flex;
    gap: 1rem;
  }

  .list > span {
    font-size: clamp(1rem, 0.0909rem + 3.6364vw, 2rem);
  }

  .list > input {
      outline: none;
      border: none;
      border-radius: .5rem;
      background: none;
      font-size: clamp(1.3rem, 0.0909rem + 3.6364vw, 2rem);
      opacity: .5;
      width: 100%;
  }
</style>
