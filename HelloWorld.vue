<template>
  <div class="todo-app">
  <h1>Todo App</h1>
  <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter your units">
  <ul>
  <li v-for="(task, index) in tasks" :key="index">
  <input type="checkbox" v-model="task.completed">
  <span :class="{ completed: task.completed }">{{ task.text }}</span>
  <button @click="removeTask(index)">Remove</button>
  </li>
  </ul>
  </div>
 </template>
  
 <script>
 export default {
  data() {
  return {
  newTask: '',
  tasks: []
  };
  },
  methods: {
  addTask() {
  if (this.newTask.trim() !== '') {
  this.tasks.push({
  text: this.newTask,
  completed: false
  });
  this.newTask = '';
  }
  },
  removeTask(index) {
  this.tasks.splice(index, 1);
  }
  }
 };
 </script>
  
 <style scoped>
 .todo-app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  font-family: Arial, Helvetica, sans-serif, sans-serif;
 }
  
 ul {
  list-style: none;
  padding: 0;
 }
  
 li {
  display: flex;
  align-items: center;
  padding: 10px;
  border: 6px solid #87fc8b;
  border-radius: 4px;
  margin: 10px 0;
 }
  
 .completed {
  text-decoration: line-through;
  color: #888888;
 }
  
 button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #09b1f3;
  border: none;
  color: rgb(234, 234, 72);
  border-radius: 4px;
  cursor: pointer;
 }
 </style>