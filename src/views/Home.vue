<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    
  </div>
</template>

<script>
import Todos from '../components/Todos';
// import Header from '../components/layout/Header';
import AddTodo from '../components/AddTodo';
import Axios from 'axios'


export default {
  name: 'Home',
  components: {
    AddTodo,
    Todos
  },
  data(){
    return {
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      console.log(id);
      Axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todos=this.todos.filter(todo=>todo.id!==id))
      .catch(err=>console.log(err) )
      
      
    },
    addTodo(newTodo){
      const {title,isCompleted}=newTodo
      Axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,isCompleted
      })
      .then(res=>this.todos=[...this.todos,res.data])
      .catch(err=>console.log(err) )
      
    },
    created(){
      Axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res=> this.todos=res.data)
      .catch(err=>console.log(err));
       
    }
    
  },
  mounted(){
      this.created() 
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

    .btn{
        background: #555;
        color: #fff;
        border: none;
        padding: 7px 20px;
        display: inline-block;
        cursor: pointer;
        /* float: right; */
    }

    .btn:hover{
      background: #666;
    }
</style>
