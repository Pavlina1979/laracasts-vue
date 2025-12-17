<script setup>
import { computed, ref } from 'vue';


const props = defineProps({
  initialTags: {
    type: Array
  },
  currentTag: {
    type: String
  }
});



let tags = computed(() => {
  return ['all', ...new Set(props.initialTags)];
});


</script>

<template>
  <div class="flex space-x-2 my-4">
    <button v-for="tag in tags" @click="$emit('change', tag)" class=" border rounded px-2 py-1 text-sm"
      :class="{ 'current-tag': tag === currentTag }">{{ tag }}</button>
  </div>
</template>