<template>
    <div class="todo-app">
      <h1>Minimalistic To-Do App</h1>
      <div class="input-group">
        <input v-model="newTodo" placeholder="New Todo" @keyup.enter="addTodo" />
        <button @click="addTodo">Add</button>
      </div>
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <span :class="{ completed: todo.completed }" @click="toggleComplete(todo)">
            {{ todo.text }}
          </span>
          <button @click="removeTodo(index)">Remove</button>
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
        if (this.newTodo.trim()) {
          this.todos.push({ text: this.newTodo, completed: false });
          this.newTodo = '';
        }
      },
      toggleComplete(todo) {
        todo.completed = !todo.completed;
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      }
    }
  };
  </script>
  
  <style scoped>
  .todo-app {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
    font-family: 'Arial', sans-serif;
    text-align: center;
  }
  
  h1 {
    color: #2c3e50;
  }
  
  .input-group {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 10px;
  }
  
  button {
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    background-color: #42b983;
    color: white;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #369e67;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #eee;
  }
  
  li:last-child {
    border-bottom: none;
  }
  
  li span {
    cursor: pointer;
  }
  
  li span.completed {
    text-decoration: line-through;
    color: #888;
  }
  
  li button {
    background-color: #e74c3c;
  }
  
  li button:hover {
    background-color: #c0392b;
  }
  </style>
  