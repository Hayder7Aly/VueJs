<template>
    <h2>{{title}}</h2>
    <p>{{body}}</p>
    <button @click="deleteTodo(todoId)">Del Todo</button>
    <button @click="editTodo(todoId)">Edit Todo</button>
    <hr />
</template>

<script>
    import {inject} from "vue"
    export default {
        name: "Todo",
        setup(){
            const deleteTodo = inject("DEL_TODO")
            const editTodo = inject("EDIT_TODO")
            return {
                deleteTodo,
                editTodo
            }
        },
        props: ["title","body","todoId"],
        
    }
</script>

<style  scoped>

</style>