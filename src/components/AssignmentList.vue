<script setup>
import { computed, ref } from 'vue';
import Assignment from './Assignment.vue';
import AssignmentTags from './AssignmentTags.vue';

let currentTag = ref('all');

const props = defineProps({
  assignments: {
    type: Array
  },
  title: {
    type: String
  }
});


let filteredAssignments = computed(() => {
  if (currentTag.value === 'all') {
    return props.assignments;
  }
  return props.assignments.filter(a => a.tag === currentTag.value);
});
</script>

<template>
  <section v-show="assignments.length">
    <h2 class="text-2xl">{{ title }} ({{ assignments.length }})</h2>

    <AssignmentTags :initialTags="assignments.map(a => a.tag)" @change="currentTag = $event" :currentTag="currentTag" />

    <ul class="border border-gray-600 divide-y divide-gray-600">
      <Assignment v-for="assignment in filteredAssignments" :assignment="assignment" :key="assignment.id" />
      <!-- <li v-for="(assignment, index) in assignments" :key="assignment.id">
        <label>
          {{ assignment.name }} <input type="checkbox" v-model="assignment.complete">
        </label>
      </li> -->
    </ul>
  </section>
</template>