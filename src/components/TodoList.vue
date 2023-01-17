<template>
   <ul>
      <TodoItem
      v-for="(todo, index) in todos"
      :todo="todo"
      :index="index"
      :key="todo.id"
      @remove-todo="$emit('remove-todo', $event)"
       />
   </ul>
</template>

<script>
   import TodoItem from '@/components/TodoItem';
   export default {
    props: [
        'todos'
    ],
    components: { 
      TodoItem
    }
}
</script>

<style scoped>
   ul {
      list-style: none;
      margin: 10;
      padding: 0;
   }
</style>