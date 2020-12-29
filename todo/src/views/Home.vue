<template>
  <div id="app">
    <div class="container">
      <Header />
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" @del-todo="deleteTodo" @completeToggle="completedChanged"/>
    </div>
  </div>
</template>

<script>
import Header from '../components/layout/Header';
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      // eslint-disable-next-line no-unused-vars
      .then(res =>  this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err.message));
    },
    completedChanged(id) {
      this.todos.map((todo) => {
        if (todo.id == id) {
          todo.completed = !todo.completed;
        }
      });
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed,
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err.message));

    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err.message));
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@400;500;700&display=swap');

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: 'Ubuntu', sans-serif;
  line-height: 1.4;
}

#app {
    background-color: #41B883;
    height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
}

.container {
  display: flex;
  flex-direction: column;
  width: 80%;
  height: 80%;
  background: #DFDFDF;
  border-radius: 12px;
  overflow: hidden;
}

.btn:hover {
  background: #666;
}
</style>
