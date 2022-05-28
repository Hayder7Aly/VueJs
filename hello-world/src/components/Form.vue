<template>
  <form @submit.prevent="addTodo({title,body})">
    <div class="box">
      <label for="title">Title</label>
      <input type="text" id="title" v-model="title"/>
    </div>
    <div class="box">
      <label for="body">Body</label>
      <input type="text" id="body" v-model="body"/>
    </div>
    <div class="box">
        <button type="submit" class="btn">Add ToDo</button>
    </div>
  </form>
</template>

<script>
import { reactive, toRefs, inject } from 'vue'
export default {
    name : "Form",
  setup() {
      const state = reactive({title : "", body : ""})

      const addTodo = inject("ADD_TODO")



      return {
          ...toRefs(state),
          addTodo
      }
  },
}
</script>

<style  scoped>
</style>