<template>
  <div v-else>
    <h1> ☠️ 👽 👾Tiko's To Do🤖 🎃 💋</h1>
    <router-link class="link" to="/">Home</router-link>
    <hr>
    <AddTodo @add-todo="addTodo"/>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <Loader v-if="loading"/>
    <ToDoList
        v-else-if="filteredTodos.length"
        v-bind:todos="filteredTodos"
        @remove-todo="removeTodo"/>
    <p v-else>Time to add some missions for ya! 😉</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import ToDoList from "@/components/ToDoList"
import AddTodo from "@/components/AddTodo"
import Loader from "@/components/Loader"


export default Vue.extend({
  name: 'App',
  data():Object {
    return {
      loading: true,
      todos : [],
      filter: "all"
    }
  },
  /*watch : {
    filter(value) {
      console.log(value)
    }
  }*/
  computed : {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }
      if (this.filter === 'not-completed') {
        return (this.todos.filter(m => !m.completed))
      }
      if (this.filter === 'completed') {
        return (this.todos.filter(m => m.completed))
      }
    }
  },
  components: {
    ToDoList,
    AddTodo,
    Loader
  },
  mounted() {
    fetch('http://my-json-server.typicode.com/Tik2004/vuetodos/todos')
        .then(response => response.json())
        .then(json => {
            this.todos=json;
            this.loading=false;

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
.link {
  text-decoration: none;
}
select {
  margin-top: .5rem;
  box-sizing: border-box;
  border: 2px solid #eee;
  padding-left:10px;
  padding-right: 10px;
  border-radius: 5px;
  transition-duration: 0.3s;
  &:focus,&:after {
    box-shadow:  0px 0px 5px 0px rgba(57,57,245,1);
    border: 2px solid rgba(57,57,245,1);
    outline: none;
  }
}
</style>
