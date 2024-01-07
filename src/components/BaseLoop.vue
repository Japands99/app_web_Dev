<script setup>
import { ref } from 'vue';

const newTask = ref('');
const tasks = ref([]);

function addTask() {
  if (newTask.value.trim() !== '') {
    tasks.value.push({
      text: newTask.value,
      completed: false
    });
    newTask.value = '';
  }
}

function deleteTask(index) {
  tasks.value.splice(index, 1);
}
</script>

<template>
  <div class="todo">
    <h1>Todo List</h1>
    <div>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" class="input">
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <input type="checkbox" v-model="task.completed">
          <span :class="{ completed: task.completed }">{{ task.text }}</span>
          
        </li>
      </ul>
    </div>
          <button @click="deleteTask(index)">Delete</button>  
  </div>
  

</template>
