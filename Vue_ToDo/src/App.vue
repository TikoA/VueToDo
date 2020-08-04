<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import ToDoList from "@/components/ToDoList"
import AddTodo from "@/components/AddTodo"

export default Vue.extend({
  name: 'App',
  data():Object {
    return {
      todos : []
    }
  },
  components: {
    ToDoList,
    AddTodo
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=30')
    .then(response => response.json())
    .then(json => {
      this.todos=json
    })
  },
  methods : {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
});
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
