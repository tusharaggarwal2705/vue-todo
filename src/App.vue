<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
    
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {
  name: 'App',
  components: {
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
