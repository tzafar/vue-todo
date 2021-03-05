<template>
  <div id="app">
    <todo-list v-bind:todos="todos"/>
    <create-todo v-on:add-todo="addTodo"></create-todo>
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
