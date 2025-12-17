<script setup>
import { computed, onMounted, ref } from 'vue';
import AssignmentList from './AssignmentList.vue';
import AssignmentCreate from './AssignmentCreate.vue';

let buttonClasses = ref('text-green');
let active = ref(false);

const assignments = ref([
  { id: 1, name: 'Finish project', complete: false },
  { id: 2, name: 'Read chapter 13', complete: false },
  { id: 3, name: 'Turn in homework', complete: false }
]);

function add(name) {
  assignments.value.push(
    { id: assignments.value.length + 1, name: name, complete: false }
  );
}

const toggleClass = function () {
  active.value = !active.value;
  // console.log(active);
  // buttonClasses.value === 'text-green' ? buttonClasses.value = 'text-red' : buttonClasses.value = 'text-green'
};

const filters = computed(() => {
  return {
    inProgress: assignments.value.filter(assignment => !assignment.complete),
    completed: assignments.value.filter(assignment => assignment.complete)
  }
});

</script>

<template>
  <!-- <button @click="toggleClass" :class="active ? 'text-green' : 'text-red'">Click me</button> -->
  <div class="space-y-6">
    <AssignmentList :assignments="filters.inProgress" title="In Progress" />
    <AssignmentList :assignments="filters.completed" title="Completed" />

    <AssignmentCreate @add="add" />

    <!-- <form @submit.prevent="add" class="border border-gray-500">
      <input v-model="newAssignment" type="text" placeholder="New assignment" class="p-2">
      <button type="submit" class="p-2 border-l border-l-gray-600">Add</button>
    </form> -->
  </div>
</template>

<style scoped>
.text-red {
  color: red;
}

.text-green {
  color: green;
}
</style>
