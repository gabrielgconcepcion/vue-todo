<template>
  <div class="ui centered card">
    <div class="content" v-show="!isEditing">
      <div class="header">
        {{todo.title}}
      </div>
      <div class="meta">
        {{todo.project}}
      </div>
      <div class="extra content">
        <span class="right floated check icon" v-on:click="uncheckTodo(todo)" v-show="todo.done">
          <i class="remove icon"></i>
        </span>
        <span class="right floated check icon" v-on:click="completeTodo(todo)" v-show="!todo.done">
          <i class="check icon"></i>
        </span>
        <span class="right floated edit icon" v-on:click="showForm">
          <i class="edit icon"></i>
        </span>
        <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
          <i class="trash icon"></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Title</label>
          <input type="text" v-model="todo.title">
        </div>
        <div class="field">
          <label>Project</label>
          <input type="text" v-model="todo.project">
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
  <div class="ui two button attached buttons">
    <div class="ui green basic button" v-show="!isEditing && todo.done" disabled>Completed</div>
    <div class="ui red basic button" v-show="!isEditing && !todo.done">Pending</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data: function () {
    return {
      isEditing: false
    }
  },
  methods: {
    uncheckTodo: function(todo){
      this.$emit('uncheck-todo',todo)
    },
    completeTodo: function(todo){
      this.$emit('complete-todo',todo)
    },
    deleteTodo: function (todo) {
      this.$emit('delete-todo', todo)
    },
    showForm: function () {
      this.isEditing = 1
    },
    hideForm: function () {
      this.isEditing = 0
    }
  }
}
</script>
