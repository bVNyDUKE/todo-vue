<template>
  <div id="app">
    <todo-list v-bind:todos="todos"></todo-list>
    <add-new-todo v-on:create-todo="addTodo"></add-new-todo>
  </div>
</template>

<script>
import AddNewTodo from './components/AddNewTodo.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList,
    AddNewTodo
  },
  methods:{
    addTodo(title){
      console.log(title)
      this.todos.push(title)
    }
  },
  data(){
    return{
      todos:[
        {
          title: 'Todo A',
          project: 'Project A',
          done: false,
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: true,
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: false,
        },
        {
          title: 'Todo D',
          project: 'Project D',
          done: false,
        },
      ]
    }
  }
}
</script>

<style>

</style>
