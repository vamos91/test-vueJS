<template>
    <div id="app">
        <AddTodo v-on: add-todo="addTask"></AddTodo>
    <todos v-bind:todos="todos" v-on:del-todo="deleteTodo"></todos>
  </div >
</template >

<script>
import todos from '../components/Todos'
import AddTodo from '../components/AddTodo'
import axios from 'axios'
    
export default {
        name: 'Home',
components: {
        todos,
        AddTodo
    },
data(){
return {
        newTodo: {},
    todos: []
    }
},
methods:{
    deleteTodo: function(id){
    axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then((response) => {
            console.log(response)
            this.todos.forEach((element, index) => {
                if (element.id === id) {
                    this.todos.splice(index, 1)
                }
            })
        })
        .catch((err) => {
            console.log(err)
        })
    },
addTask: function(newTodo){
        axios.post('https://jsonplaceholder.typicode.com/todos', newTodo)
            .then((response) => {
                console.log(response)
            })
            .catch((err) => {
                console.log(err)
            })
    this.todos.push(newTodo)
    }
},
created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then((response) => {
            console.log(response.data)
            this.todos = response.data
        })
        .catch((err) => {
            console.log(err)
            })
    }
    }
</script>

    <style>
        *{
        padding: 0;
        margin: 0;
        box-sizing: border-box;
      }
      
body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
      }
</style>
