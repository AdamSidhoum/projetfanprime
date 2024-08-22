<template>
  <div id="app">
    <h1>Todo List</h1>
    <TaskForm @add-task="addTask" />
    <TaskList 
      :tasks="tasks" 
      @delete-task="deleteTask" 
      @toggle-task="toggleTask" 
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue'
import TaskForm from './components/TaskForm.vue'

const tasks = ref([
  { id: 1, name: 'Tâche 1', completed: false },
  { id: 2, name: 'Tâche 2', completed: false },
])

function addTask(taskName) {
  const newTask = {
    id: Date.now(),
    name: taskName,
    completed: false
  }
  tasks.value.push(newTask)
}

function deleteTask(taskId) {
  tasks.value = tasks.value.filter(task => task.id !== taskId)
}

function toggleTask(taskId) {
  const task = tasks.value.find(task => task.id === taskId)
  if (task) {
    task.completed = !task.completed
  }
}
</script>