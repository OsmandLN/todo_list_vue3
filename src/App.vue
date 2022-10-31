<template>
  <div>
    <input type="text" v-model="newTodo">
    <button @click="addTodo">Add</button>
    <TodoItem v-for="todo in todos" :key="todo.id" :initial-todo="todo" @delete="removeTodo(todo)" />
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'
const { v4: uuidv4 } = require('uuid')

export default {
  name: 'App',
  components: {
    TodoItem
  },
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      const todo = { id: uuidv4(), content: '' }
      todo.content = this.newTodo
      if (todo.content.trim() === '') {
        return
        // console.log("yes")
      } else {
        this.todos.push(todo)
        console.log(this.todos)
        // console.log(uuidv4())
        console.log(todo)
        this.newTodo = ''
      }
    },
    removeTodo(todo) {
      console.log('del')
      this.todos = this.todos.filter(unwantedTodo => unwantedTodo.id !== todo.id)
    }
  }
}
</script>

<style>

</style>
