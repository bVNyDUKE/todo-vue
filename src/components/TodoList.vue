<template>
    <div>
        <p>Completed Tasks: {{ todos.filter(todo => todo.done === true).length }} </p>
        <p>Pending Tasks: {{ todos.filter(todo => todo.done === false).length }} </p>
        <todo-item v-for="(todo, index) in todos" :key="index" :todo="todo" v-on:delete-todo="deleteTodo(todo)"></todo-item>
        
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    props:['todos'],
    components:{
        TodoItem,
    },
    methods:{
        deleteTodo(todo){
            const todoIndex = this.todos.indexOf(todo)
            this.todos.splice(todoIndex, 1)
        },
    }
}
</script>

<style>

</style>