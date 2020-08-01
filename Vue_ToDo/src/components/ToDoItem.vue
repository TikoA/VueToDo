<template>
    <ul>
      <li>
        <span v-bind:class="{done: todo.completed}">
          <input v-if="!todo.completed" type="checkbox" v-on:change="todo.completed = !todo.completed">
          <b>{{index+1}}</b>
          {{todo.title}}
        </span>
      <button v-on:click="$emit('remove-todo',todo.id)" class="rm">&times;</button>
      </li>
    </ul>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props: {
      todo: {
        type:Object,
        required:true
      },
      index: Number
    }
})
</script>

<style lang="less">
  ul {
    list-style: none;
    li {
      font-family: "Ubuntu Mono";
      border: 1px solid #ccc;
      display:flex;
      justify-content: space-between;
      padding: .5rem 2rem;
      margin-bottom: 1rem;
    }
    .rm {
      background: red;
      color: #fff;
      border-radius: 50%;
      font-weight: bold;
      border: 0;
    }

    input {
      margin-right: 1rem;
    }
    .done {
      text-decoration: line-through;
    }
  }
</style>