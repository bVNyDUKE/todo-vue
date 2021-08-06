<template>
    <div>
        <todo-item v-for="(todo, index) in todos" :key="index" :todo="todo" @delete-todo="deleteTodo(todo)" @complete-todo='completeTodo(todo)'></todo-item>
        <add-new-todo v-on:create-todo='addTodo'></add-new-todo>
    </div>
</template>

<script>
import AddNewTodo from './AddNewTodo.vue'
import TodoItem from './TodoItem.vue'

export default {
    props:['todos'],
    components:{
        TodoItem,
        AddNewTodo,
    },
    methods:{
        deleteTodo(todo){
            const todoIndex = this.todos.indexOf(todo)
            this.todos.splice(todoIndex, 1)
        },
        addTodo(item){
            this.todos.push(item)
        },
        completeTodo(item){
            const todoIndex = this.todos.indexOf(item)
            this.todos[todoIndex].done = !this.todos[todoIndex].done
        }
    }
}
</script>

<style>

</style>