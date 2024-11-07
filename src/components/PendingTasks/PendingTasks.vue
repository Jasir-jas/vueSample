<script setup>
import "font-awesome/css/font-awesome.css";
import { defineProps } from "vue";

const props = defineProps({
  tasks: Array,
  Required: true,
});

const deleteTask = (index) => {
  alert(index);
};
</script>

<template>
  <div class="p-6 w-full bg-white rounded-lg shadow-lg">
    <!-- Heading -->
    <h2 class="text-2xl font-semibold mb-6 text-center">ToDo List</h2>

    <!-- Task List (Take full width) -->
    <ul class="space-y-4 w-full">
      <!-- Single task item -->
      <li
        v-for="(task, index) in props.tasks"
        class="flex justify-between items-center p-4 border border-gray-300 rounded-lg hover:bg-gray-100"
      >
        <span class="text-lg text-gray-800">{{ task }}</span>
        <button class="flex">
          <i
            @click="deleteTask(index )"
            class="fa fa-trash hover:text-red-500"
            style="font-size: 1.5rem"
          ></i>
          <i
            class="fa fa-edit ml-2 hover:text-blue-500"
            style="font-size: 1.5rem"
          ></i>

          <!-- You can add icon here -->
        </button>
      </li>
    </ul>

    <!-- Message when no tasks are present -->
    <p v-if="props.tasks.length === 0" class="text-center text-gray-500 mt-6">
      No pending tasks!
    </p>
  </div>
</template>

<style scoped>
/* Optional: Add custom styles here if needed */
</style>
