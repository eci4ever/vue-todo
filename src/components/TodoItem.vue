<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
  </div>
</template>
<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    data () {
        let data = { id: '' };
        data = Object.assign({}, data, this.todo);
        return data
        //Data reactivity
        //https://vuejs.org/v2/guide/reactivity.html
        //https://medium.com/@stefanledin/how-to-properly-add-props-to-data-object-in-vue-js-f886307a509
    },
    methods: {
        markComplete() {
            if(this.completed == 1) {
                this.completed = null
            } else {
                this.completed = true
            }
            let updateTodo = {
                id: this.id,
                title: this.title,
                completed: this.completed
            }
            this.$emit('update-todo', updateTodo);
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>
<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10;
    border-bottom: 1px #ccc dotted;
}
.is-complete {
    text-decoration: line-through;
}
.del {
    background: red;
    color: white;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>