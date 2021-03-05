<template>
    <div>
        <p>Completed Tasks: {{todos.filter(todo => todo.done === true).length}}</p>
        <p>Pending Tasks: {{todos.filter(todo => todo.done === false).length}}</p>
        <div class="ui centered card">
            <todo @edit-todo="editTodo" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos"
                  v-bind:key="todo" v-bind:todo="todo"></todo>
        </div>
    </div>
</template>

<script type="text/javascript">
    import Todo from './Todo'

    export default {
        name: 'TodoList',
        components: {Todo},
        props: ['todos'],
        methods: {
            deleteTodo(todo) {
                this.$emit('delete-todo-list', todo)
            },
            completeTodo(todo) {
                this.$emit('complete-todo-list', todo)
            },
            editTodo(updatedTodo){
                this.$emit('edit-todo-list', updatedTodo)
            }
        }
    }
</script>

