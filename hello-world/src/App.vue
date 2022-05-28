<template>
  <div>
    <h1 class="heading">{{ todos }} ToDo App</h1>
    <button @click="show = !show">Want to add Todo !</button>
    <Form v-show="show" />
    <h1>Todo List</h1>
    <TodoList :todos="todos" name="Hayder" />
  </div>
</template>

<script >
import { reactive, toRefs, provide, ref } from 'vue'
import Form from './components/Form.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    Form,
    TodoList,
  },
  setup() {
    const state = reactive({
      todos: [{ id: 1, title: 'todo 1', body: 'body 1' }],
      editTodo : {}
    })
    const show = ref(false)

    function addTodo(todo) {
      state.todos.push({ id: state.todos.length + 1, ...todo })
    }

    function deleteTodo(todoId) {
      state.todos = state.todos.filter((todo) => todo.id !== todoId)
    }

    function editTodo(todoId, newData){
      state.todos = state.todos.map(todo => todo.id ===  todoId ? {id: todoId, ...newData}: todo)
    }

    provide('ADD_TODO', addTodo)
    provide('DEL_TODO', deleteTodo)
    provide('EDIT_TODO', editTodo)

    return {
      ...toRefs(state),
      show,
    }
  },
}
</script>

<style  scoped>
.heading,
h1 {
  text-align: center;
  color: #333;
  font-size: 30px;
}
</style>