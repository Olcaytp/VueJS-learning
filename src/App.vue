<script setup lang="ts">
import DashboardLayout from './components/DashboardLayout.vue'
</script>

<template>
  <DashboardLayout />
</template>

<style>
body {
  background-color: #111827;
  color: #f3f4f6;
}

button {
  background-color: #3b82f6;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s;
}

button:hover {
  background-color: #2563eb;
}

button:disabled {
  background-color: #6b7280;
  cursor: not-allowed;
}
</style>