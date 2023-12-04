<template>
  <main>
    <div class="container grid-row-4">
      <section class="input-area">
          <label for="todo" style="color: #153266;">Enter a task</label>
          <input type="text" v-model="todo" @keyup.enter="addTodo" />
          <AddButton @add-my-todo="addTodo"></AddButton>
      </section>
      <section>
        <h2 style="color: #153266;">ToDo List</h2>
        <ul class="lists">
          <Lists :todo="this.todo" :todos="this.todos"></Lists>
        </ul>
      </section>
    </div>
  </main>
</template>

<script>
import AddButton from "./AddButton.vue";

import Lists from "./Lists.vue";

export default {
  name: "TodoList",
  data() {
    return {
      todos: [],
      todo: "",
    };
  },

  components: {
    AddButton,
    Lists,
  },

  methods: {
    addTodo() {
      if (this.todo.trim() !== "") {
        this.todos.push({
          text: this.todo,
          isEditing: false,
          editedText: "",
        });
        this.todo = "";
      } else {
        alert("Add an item");
      }
    },

    
  },
};
</script>

<style scoped>

  .grid-row-4 {
    display: grid;
    gap: min(10vh, 2rem);
  }
  .input-area {
    display: flex;
    justify-content: space-between;
    gap: 1.5rem;
    align-items: center;
  }

  .input-area > label {
    font-size: clamp(1rem, 0.0909rem + 3.6364vw, 2rem);
    font-weight: bold;
  }

  .input-area > input {
    flex-grow: 1;
    font-size: clamp(.5rem, 0.0909rem + 3.6364vw, 1.3rem);
  }

  section:has(h2) {
    display: grid;
  }

  section:has(h2) > h2 {
    font-size: min(10vw + 1rem, 3rem);
    text-align: center;
    font-weight: bold
  }

  .lists {
    display: grid;
    gap: 1rem;
  }
</style>
