<template>
  <h2>Todo List</h2>
  <button @click="getTodoList">Request Todo</button>
  <ul>
    <li v-for="todo in todoList" :key="todo.id">{{ todo.title }}</li>
  </ul>
  <div>
    <label for="todo">할일</label>
    <input type="text" v-model="todoItem.title" />
    <button @click="createTodo">제출</button>
  </div>

  <p v-if="errorMessage">{{ errorMessage }}</p>
</template>

<script>
import axios from "axios";
export default {
  name: "todoList",
  data() {
    return {
      todoList: [],
      errorMessage: "",
      todoItem: {
        title: "",
        completed: false,
      },
    };
  },
  methods: {
    // get방식
    getTodoList() {
      const url = "https://jsonplaceholder.typicode.com/tod11os";
      axios
        .get(url)
        .then((res) => (this.todoList = res.data))
        .catch((e) => (this.errorMessage = "에러가 발생했습니다"));
    },
    // post방식
    createTodo() {
      const url = "https://jsonplaceholder.typicode.com/todos";
      axios
        .post(url, this.todoItem)
        .then((res) => console.log(res))
        .catch((e) => console.log(e));
    },
  },
};
</script>

<style></style>
