<template>
  <div class="task-list">
    <ul>
      <li 
        v-for="task in tasks" 
        :key="task.id" 
        :class="{ completed: task.completed }"
      >
        <input 
          type="checkbox" 
          :checked="task.completed" 
          @change="$emit('toggle-task', task.id)"
        />
        <span>{{ task.name }}</span>
        <button @click="$emit('delete-task', task.id)">✖</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  tasks: Array
})
</script>