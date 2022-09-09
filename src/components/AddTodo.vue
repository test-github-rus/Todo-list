<template>
   <form @submit.prevent="newTodo">
      <input v-model="text" type="text" placeholder="добавить задачу">
      <button type="submit">Добавить</button>
   </form>
</template>

<script>
   export default {
      data() {
         return{
            text: '' 
         }
      },
      methods: {
         newTodo() {
            if(this.text.trim() != '') {
               let newTodo = {
                  id: Date.now(), 
                  title: this.text, 
                  completed: false
               };
                this.$emit('add-todo', newTodo)
                this.text = ''
            }
         }
      }
   }
</script>

<style scoped>
   form {
      display: flex; 
      width: 300px;
      height: 30px;
      margin-bottom: 1rem;
   }
</style>