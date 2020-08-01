<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <br>
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title:""
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo',newTodo)
        this.title=""
      }
    }
  }
}
</script>

<style lang="less">
  form {
    input {
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
    button {
      background-color:#44c767;
      border-radius:28px;
      border:1px solid #18ab29;
      display:inline-block;
      cursor:pointer;
      color:#ffffff;
      margin-top: .5rem;
      font-family:"Ubuntu Mono";
      font-size:17px;
      font-weight:bold;
      padding:1px 22px;
      text-decoration:none;
      text-shadow:0px 1px 0px #2f6627;
    }

    button:hover {
      background-color:#5cbf2a;
    }
    button:active {
      position:relative;
      top:1px;
    }
  }
  * {
    outline: none;
  }
</style>