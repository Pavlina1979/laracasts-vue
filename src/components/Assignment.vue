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
      {{ assignment.name }} <div class="flex items-center space-x-1">
        <span class="text-xs">{{ assignment.tag }}</span> <input type="checkbox" v-model="assignment.complete">
      </div>
    </label>
  </li>
</template>