<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';

export default {
  name: 'App',
  components: {
    Header,
    Todos
  },
  data(){
    return {
      todos:[
        {
          _id:1,
          title:'create user-interface',
          isCompleted:false
        },
        {
          _id:2,
          title:'create back-end',
          isCompleted:false
        },
        {
          _id:3,
          title:'create front-end',
          isCompleted:false
        }
      ]
    }
  },
  methods:{
    deleteTodo(id){
      this.todos=this.todos.filter(todo=>todo._id!==id)
      
    }
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
  line-height: 1.4;
}
</style>
