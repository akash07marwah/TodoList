<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos  v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos  from "../components/Todos";
import AddTodo from '../components/AddTodo';
import axios from 'axios';
import { debuglog } from 'util';
export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data(){
    return {
      todos:[{
        id:1,
        title:'Complete Coding Assignment!',
        completed:false
      },{
        id:2,
        title:'Complete Homework!',
        completed:false
      },{
        id:3,
        title:'Complete Vue App!',
        completed:false
      } ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id!=id );
    },
    addTodo(newTodo){
      this.todos = [...this.todos,newTodo];
    }
    
  // created(){
  //     console.log('Created') 
  //         axios
  //         .get('https://jsonplaceholder.typicode.com/todos') 
  //         .then( (res) => this.todos = res.data) 
  //         .catch(err => console.log(err))
  //  return true
  //  }

  }
}
</script>

<style>
  *{
      box-sizing:border-box;
      margin:0;
      padding:0;
  }
  body{
    font-family:Arial, Helvetica, sans-serif;
    line-height:1.4;
  }
  .btn{
    display: inline-block;
    border:none;
    background: #555;
    color:#fff;
    padding: 7px 20px;
    cursor:pointer;
  }
  .btn:hover{
    background: #666;
  }
</style>
