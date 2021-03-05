<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => todo.done === false).length}}</p>
    <div class="ui centered card" >
      <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
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
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
      },
      completeTodo(todo) {
        const index = this.todos.indexOf(todo)
        this.todos[index].done = true
      }
    }
  }
</script>

