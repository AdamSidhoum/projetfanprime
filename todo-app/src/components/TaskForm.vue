<template>
    <form @submit.prevent="submitTask" class="task-form">
      <input 
        v-model="taskName" 
        placeholder="Ajouter une nouvelle tâche" 
        aria-label="Ajouter une nouvelle tâche"
      />
      <button type="submit">Ajouter</button>
    </form>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const taskName = ref('')
  
  function submitTask() {
    if (taskName.value.trim()) {
      emit('add-task', taskName.value)
      taskName.value = ''
    }
  }
  
  const emit = defineEmits(['add-task'])
  </script>