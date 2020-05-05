<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/> <!-- being passed in as a prop -->
  </div>
</template>

<script>
import AddTodo from './components/AddTodo';
import Header from './components/layout/header';
import Todos from './components/Todos';

export default {
  name: 'App',
  components: {
    AddTodo,
    Header,
    Todos
  },
  data () { // data is a function that returns an object
    return {
      todos: [ // array of 3 todo objects
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]

    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id); // loops through but with condition and returns an array based on that condition
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo]
    }
  }
}
</script>

<style> 
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
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
  background: #666;
}
</style>
