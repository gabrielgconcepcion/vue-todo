<template>
  <div>
    <todo-list :todos="todos"></todo-list>
    <create-todo @add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data: function () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: false
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false
      }]
    }
  },
  methods: {
    addTodo: function (todo) {
      console.log(todo);
      this.todos.push(todo)
    }
  }
}
</script>

<style>
</style>
