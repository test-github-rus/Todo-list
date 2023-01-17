<template>
   <select v-model="selected" @change="$emit('select-todo', selected)">
      <option value="all">Все</option>
      <option value="completed">Выполненные</option>
      <option value="not-completed">Не выполненные</option>
   </select>
</template>

<script>
export default {
   data() {
      return{
        selected: 'all'
      }
   }
} 
</script>
