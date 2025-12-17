<script setup>

const props = defineProps({
  assignment: {
    type: Object
  }
})
</script>

<template>
  <li>
    <label class="px-2 py-1 flex justify-between gap-2 items-center">
      {{ assignment.name }} <input type="checkbox" v-model="assignment.complete">
    </label>
  </li>
</template>