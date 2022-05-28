<template>
    <div class="todo_container">
        <div class="todo"  v-for="todo in todos" :key="todo.id">
             <Todo :title="todo.title" :body="todo.body" :todoId="todo.id" />
        </div>

   </div>
</template>

<script>
import Todo from "./Todo.vue"
export default {
  name: 'TodList',
  components: {
      Todo
  },


  props: ["todos"],




}
</script>

<style  scoped>
</style>