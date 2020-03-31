<template>
    <div>
        <div v-bind:key="todo._id" v-for="todo in todos">
            <!-- <h3>{{todo.title}}</h3> -->
            <TodoItem v-bind:todo="todo"/>
        </div>
    </div>
</template>

<script>

import TodoItem from './TodoItem.vue'
export default {
    name:"Todos",
    components:{
        TodoItem
    },
    props:["todos"]
}
</script>

<style scoped>
 
</style>