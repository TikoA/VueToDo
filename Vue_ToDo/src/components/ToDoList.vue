<template>
    <div>
       <ToDoItem v-for="(todo,i) of todos"
       v-bind:todo="todo"
       v-bind:index="i"
       v-on:remove-todo="removeTodo"/>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import ToDoItem from "@/components/ToDoItem"
export default Vue.extend({
    props:["todos"],
    components : {
        ToDoItem
    },
    methods: {
      removeTodo(id) {
        this.$emit('remove-todo',id)
      }
    },
})
</script>