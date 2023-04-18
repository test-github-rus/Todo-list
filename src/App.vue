<template>
  <div id="app">
    <h1>Список дел</h1>
    <hr>
     <strong>Всего: {{filteredTodos.length}}</strong>
      <AddTodo
      @add-todo="addTodo"
      />
      <TodoItemSelect 
      @select-todo="selectTodo"
      />
      <hr>
      <TodoList
        v-if="filteredTodos.length != 0"
        :todos="filteredTodos"
        @remove-todo="removeTodo"
      />
      <p v-else>Список пуст</p>
    <hr>
  </div>
</template>

<script>
  import TodoList from '@/components/TodoList';
  import AddTodo from '@/components/AddTodo';
  import TodoItemSelect from '@/components/TodoItemSelect';
  export default {
    name: 'App',
    data() {
      return{
        value:'all',
        todos: [
          {id: 1, title: 'создать приложение "Todo List" на JS', completed: true},
          {id: 2, title: 'создать приложение "Todo List" на  VUE', completed: true},
          {id: 3, title: 'добавить VUEX', completed: false},
          {id: 4, title: 'добавить VUETIFY', completed: false}
        ]
      }
    },
    methods: {
      removeTodo(index) {
         this.filteredTodos.splice(index, 1)
      },
      addTodo(newTodo) {
        this.filteredTodos.push(newTodo)
      },
      selectTodo(selected) {
        this.value=selected
      }
    },
    computed: {
      filteredTodos() {
        if(this.value == 'all') {
          return this.todos
        } else if(this.value == 'completed') {
          return this.todos.filter(item => item.completed == true)
        } else {
          return this.todos.filter(item => item.completed == false )
        }
      }
    },
    components: {
      TodoList, AddTodo, TodoItemSelect
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
