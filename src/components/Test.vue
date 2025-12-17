<script setup>
import { computed, onMounted, ref } from 'vue';

let buttonClasses = ref('text-green');
let active = ref(false);

const assignments = ref([
  { id: 1, name: 'Finish project', complete: false },
  { id: 2, name: 'Read chapter 13', complete: false },
  { id: 3, name: 'Turn in homework', complete: false }
]);

const toggleClass = function () {
  active.value = !active.value;
  // console.log(active);
  // buttonClasses.value === 'text-green' ? buttonClasses.value = 'text-red' : buttonClasses.value = 'text-green'

};

const inProgressAssignments = computed(() => {
  return assignments.value.filter(assignment => !assignment.complete)
});

const completedAssignments = computed(() => {
  return assignments.value.filter(assignment => assignment.complete)
});
</script>

<template>
  <!-- <button @click="toggleClass" :class="active ? 'text-green' : 'text-red'">Click me</button> -->

  <section v-show="inProgressAssignments.length">
    <h2 class="text-2xl">In progress</h2>
    <ul>
      <li v-for="(assignment, index) in inProgressAssignments" :key="assignment.id">
        <label>
          {{ assignment.name }} <input type="checkbox" v-model="assignment.complete">
        </label>
      </li>
    </ul>
  </section>

  <section v-show="completedAssignments.length" class="mt-10">
    <h2 class="text-2xl">Completed</h2>
    <ul>
      <li v-for="(assignment, index) in completedAssignments" :key="assignment.id">
        <label>
          {{ assignment.name }} <input type="checkbox" v-model="assignment.complete">
        </label>
      </li>
    </ul>
  </section>

</template>

<style scoped>
.text-red {
  color: red;
}

.text-green {
  color: green;
}
</style>
