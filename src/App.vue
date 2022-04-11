<template>
  <div>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  data(){
    return {
      todos:[
      ]
    }
  },
  components: {
    Todos,
    AddTodo
  },
  methods:{

    addTodo(newTodo){
      this.todos = [...this.todos,newTodo]
    },
    deleteTodo(id){
      this.todos = this.todos.filter((todo) => todo.id !== id)
    }
  }
};
</script>
