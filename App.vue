
<template>
  <div class="todo-app">
    <h1>Todo App</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" class="input-field" placeholder="Add a task">
    <ul>
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <span>{{ todo.text }}</span>
        <button @click="deleteTodo(index)" class="delete-button">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.custom-todo-app {
  font-family: 'Verdana', sans-serif; /* Changed the font */
  max-width: 700px; /* Adjusted the max width */
  margin: 0 auto;
  padding: 30px; /* Increased padding */
  background-color: #FFD700; /* Changed the background color to gold */
  border-radius: 20px; /* Increased border radius */
  box-shadow: 0px 12px 24px rgba(0, 0, 0, 0.3); /* Increased box shadow */
  text-align: center;
}

h1 {
  font-size: 48px; /* Increased font size */
  margin-top: 10px;
  margin-bottom: 30px; /* Increased margin-bottom */
  color: #333;
}

ul {
  list-style-type: none;
  padding: 0;
}

.custom-todo-item { /* Updated list item class */
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px; /* Increased margin-bottom */
  padding: 20px; /* Increased padding */
  background-color: #FFA07A; /* Changed the list item background color to light salmon */
  border-radius: 15px; /* Increased border radius */
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2); /* Increased box shadow */
}

.custom-input-field { /* Updated input class */
  width: 100%;
  padding: 15px; /* Increased padding */
  border: 2px solid #8A2BE2; /* Changed input border color to blue violet */
  border-radius: 15px; /* Increased border radius */
  margin-bottom: 20px;
}

.custom-input-field::placeholder {
  color: #8A2BE2; /* Changed placeholder text color to match the input border color */
}

.custom-delete-button { /* Updated button class */
  background-color: #FF4500; /* Changed delete button background color to orange red */
  color: #fff;
  border: none;
  border-radius: 15px; /* Increased border radius */
  padding: 10px 18px; /* Adjusted button padding */
  cursor: pointer;
  font-size: 16px; /* Increased font size */
}

.custom-delete-button:hover {
  background-color: #CD5C5C; /* Changed delete button hover color to Indian red */
}
</style>
