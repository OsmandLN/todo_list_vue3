<template>
  <div>
    <input type="text" v-model="newTodo">
    <button @click="addTodo">Add</button>
    <ul>
      <TodoItem v-for="todo in todos" :key="todo.id" :initial-todo="todo" @delete="removeTodo(unwantedTodo)" />
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'
import { v4 as uuidv4 } from 'uuid'

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
      if (this.newTodo.trim() === '') {
        return
      }
      const todo = { id: uuidv4(), content: '' }
      todo.content = this.newTodo
      this.todos.push(todo)
      console.log('todos', this.todos)
      // console.log(uuidv4())
      console.log(todo)
      this.newTodo = ''
    },
    removeTodo(unwantedTodo) {
      console.log('del')
      this.todos = this.todos.filter(todo => todo.id !== unwantedTodo.id)
    }
  }
}
</script>

<style>

</style>
