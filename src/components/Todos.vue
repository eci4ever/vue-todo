<template>
    <div>
        <div v-for="todo in todos" v-bind:key="todo.id">
            <TodoItem v-bind:todo="todo" 
            v-on:del-todo="$emit('del-todo', todo.id)" 
            v-on:update-todo="updateTodo" />
        </div>
    </div>
</template>
<script>
import TodoItem from "./TodoItem";

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    data () {
        return {
            timer: ''
        }
    },
    props: ["todos"],
    methods: {
        updateTodo(updateTodo) {
            this.$emit('update-todo', updateTodo)
        }
    }
}
</script>
<style scoped>

</style>