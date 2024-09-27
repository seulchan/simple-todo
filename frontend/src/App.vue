<template>
  <div id="app" class="container">
    <h1 class="title">Simple To-do App</h1>
    <add-todo @add-todo="addTodo"></add-todo>
    <todo-list :todos="todos" @delete-todo="deleteTodo"></todo-list>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    AddTodo,
    TodoList
  },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem('todos')) || []
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
      this.saveTodos();
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
      this.saveTodos();
    },
    saveTodos() {
      localStorage.setItem('todos', JSON.stringify(this.todos));
    }
  }
};
</script>

<style>
.container {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  font-size: 2em;
  color: #333;
  margin-bottom: 20px;
  font-family: 'Arial', sans-serif;
}

.todo-list-title {
  text-align: center;
  font-size: 2em;
  color: #333;
  margin-bottom: 10px;
  font-family: 'Arial', sans-serif;
}
</style>
