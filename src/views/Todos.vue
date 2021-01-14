<template>
  <div>
    <h2>Hello world!</h2>
    <router-link to='/todo-vue/' class="linka">Home</router-link>
    <AddTodo @add-todo='AddTodo'/>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <hr>
    <Loader v-if="loading" />
    <TodoList 
        v-else-if='filteredTodos.length'
        v-bind:todos="filteredTodos" 
        @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>
<style scoped>
  .linka{
      color: tomato;
      text-decoration: none;
      font-weight: 600;
      font-size: 18px;
      border: orangered 1px solid;
      border-radius: 3px;
      padding: 5px;
      cursor: pointer;
  }
</style>
<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
          setTimeout(() => {
            this.todos = json
            this.loading = false
          }, 1000)
        })
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }
      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-completed'){
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  components: {
    TodoList, AddTodo, Loader
  },
  methods: {
      removeTodo(id) {
          this.todos = this.todos.filter(t => t.id !== id)
      },
      AddTodo(todo){
        this.todos.push(todo)
      }
  }
}
</script>
