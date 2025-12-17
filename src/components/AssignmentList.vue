<script setup>
import Assignment from './Assignment.vue';

const props = defineProps({
  assignments: {
    type: Array
  },
  title: {
    type: String
  }
})
</script>

<template>
  <section v-show="assignments.length">
    <h2 class="text-2xl">{{ title }}</h2>
    <ul class="border border-gray-600 divide-y divide-gray-600">
      <Assignment v-for="assignment in assignments" :assignment="assignment" :key="assignment.id" />
      <!-- <li v-for="(assignment, index) in assignments" :key="assignment.id">
        <label>
          {{ assignment.name }} <input type="checkbox" v-model="assignment.complete">
        </label>
      </li> -->
    </ul>
  </section>
</template>