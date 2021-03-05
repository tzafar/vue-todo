<template>
  <div id="app">
    <todo-list v-bind:todos="todos" v-on:delete-todo-list="deleteTodo" v-on:complete-todo-list="completeTodo"/>
    <create-todo @:add-todo="addTodo" @delete-todo="deleteTodo" ></create-todo>
  </div>
</template>

<script>
  import TodoList from './components/TodoList'
  import CreateTodo from './components/CreateTodo'

  export default {
    name: 'App',
    components: {
      TodoList,
      CreateTodo
    },
    data () {
      return {
        todos: [
          {
            title: 'Task A',
            project: 'Project 1',
            done: false
          }, {
            title: 'Task B',
            project: 'Project 2',
            done: false
          }, {
            title: 'Task C',
            project: 'Project 2',
            done: false
          }, {
            title: 'Task D',
            project: 'Project 3',
            done: false
          }
        ]
      }
    },
    methods: {
      addTodo(todo){
        this.todos.push(todo)
      },
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

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
