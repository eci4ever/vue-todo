<template>
    <div>
        <AddTodo v-on:add-todo="addTodo" />
        <Todos v-bind:todos="todos" 
        v-on:del-todo="deleteTodo" v-on:update-todo="updateTodo" />
    </div>
</template>
<script>
import Todos from "../components/Todos"
import AddTodo from "../components/AddTodo"
import axios from 'axios'

export default {
    name: 'Home',
    components: {
        Todos,
        AddTodo
    },
    data () {
        return {
        todos: []
        }
    },
    methods: {
        deleteTodo(id) {
            axios.delete(`http://192.168.0.112:8000/api/v1/todos/${id}`)
            .then(this.todos = this.todos.filter(todo => todo.id !== id))
            .catch(err => console.log(err))
        },
        addTodo(newTodo) {
        const { title, completed } = newTodo

        axios.post('http://192.168.0.112:8000/api/v1/todos', {
            title,
            completed
        })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))
        },
        updateTodo(updateTodo) {
            const { id, title, completed } = updateTodo
            axios.put(`http://192.168.0.112:8000/api/v1/todos/${id}`, {
                title,
                completed
            })
            .then()
            .catch(err => console.log(err))
        }
    },
    created () {
        axios.get('http://192.168.0.112:8000/api/v1/todos')
        .then(res => this.todos = res.data)
        .catch(err => console.log(err))
    }
}
</script>