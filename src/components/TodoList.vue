<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done=== true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done=== false}).length}}</p>
    <todo @uncheck-todo=uncheckTodo @complete-todo="completeTodo" @delete-todo="deleteTodo" v-for="todo in todos" :todo="todo"></todo>
  </div>
</template>

<script>
import Todo from './Todo'
export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    uncheckTodo:function(todo){
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = false
    },
    completeTodo:function(todo){
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
    },
    deleteTodo: function (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    }
  }
}
</script>
