<script setup>
const emit = defineEmits(['add']);
let newAssignment = '';

const addAssignment = () => emit('add', newAssignment);
</script>

<template>
  <form @submit.prevent="addAssignment" class="border border-gray-500">
    <input v-model="newAssignment" type="text" placeholder="New assignment" class="p-2">
    <button type="submit" class="p-2 border-l border-l-gray-600">Add</button>
  </form>
</template>