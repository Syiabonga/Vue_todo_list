<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="AddTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import Header from './components/layout/Header.vue';
import AddTodo from './components/AddTodo.vue';
import axios from 'axios';


export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods:{
    //Filter all the item that have a id different than the one passed in the parameters
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    AddTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
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
