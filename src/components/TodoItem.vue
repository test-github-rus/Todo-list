<template>
   <li>
      <span :class="{done: todo.completed}">
         <input type="checkbox" v-model="todo.completed"> 
         {{index + 1}}
         {{todo.title}}
      </span>
      <button class="rm" @click="$emit('remove-todo', index)">&times;</button>
   </li>
</template>

<script>
   export default {
      props: [
         'todo', 'index'
      ]
   }
</script>

<style scoped>
   li{
      border: 1px solid #ccc;
      display: flex;
      justify-content: space-between;
      padding: 0.5rem 2rem;
      margin-bottom: 1rem;
   }

  .rm{
      background: rgb(218, 32, 79);
      color: #fff;
      border-radius: 50%;
      font-weight: bold;
   }

   input{
      margin-right: 1rem;
   }

   .done{
      text-decoration: line-through;
   }

</style>
