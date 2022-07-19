<template>
  <div id="app">
    <HeaderSection />
    <AddTodo v-on:add-todo="addTodo" />
    <ViewTodos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import HeaderSection from '@/components/layout/HeaderSection';
import ViewTodos from '@/components/ViewTodos';
import AddTodo from '@/components/AddTodo';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    HeaderSection,
    ViewTodos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then((response) => (this.todos = this.todos.filter((todo) => todo.id !== response.id)))
        .catch((err) => console.log(err));
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed,
        })
        .then((response) => (this.todos = [...this.todos, response.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    // its get called automatically when the page loads just
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=0')
      .then((response) => (this.todos = response.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  margin: 10px 10%;
  border: 2px solid black;

  box-shadow: 2px 10px 20px 5px rgb(5, 188, 220);
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: rgb(118, 127, 128);
}
</style>
