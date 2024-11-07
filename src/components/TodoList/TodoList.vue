<script setup>
import { ref } from "vue";
import PendingTasks from "../PendingTasks/PendingTasks.vue";

// Store All tasks
let tasks = ref([]);

// store new task
const newTask = ref("");

// Add task fnctionality
const addTask = () => {
  if (newTask.value !== "") {
    tasks.value.push(newTask.value);
    console.log("Tasks:", tasks.value);

    newTask.value = "";
  }
};
</script>

<template>
  <!-- Wrapper div to center content -->
  <div class="flex items-center justify-center min-h-screen bg-red-300">
    <!-- Content div -->
    <div class="flex flex-col items-center w-full max-w-md">
      <!-- Heading -->
      <h1 class="text-lg mb-4 text-white">ToDo List</h1>

      <!-- Input and button wrapper -->
      <div class="flex w-full space-x-2 mb-4">
        <!-- Input -->
        <input
          type="text"
          placeholder="Enter your task"
          v-model="newTask"
          class="flex-1 h-10 border border-gray-300 rounded px-2 focus:border-transparent focus:outline-none"
        />

        <!-- Button -->
        <button
          class="h-10 px-4 bg-red-300 text-white rounded"
          @click="addTask"
        >
          ADD
        </button>
      </div>

      <!-- Pending Tasks Section aligned to the bottom -->
      <div class="flex-grow w-full flex justify-end">
        <PendingTasks :tasks="tasks" />
      </div>
    </div>
  </div>
</template>
