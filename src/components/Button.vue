<script setup>

const props = defineProps({
  buttonType: {
    type: String,
    default: 'primary'
  }
})
</script>

<template>
  <button :class="{
    'border rounded px-3 py-2': true,
    'bg-blue-200 hover:bg-blue-500 text-black': props.buttonType === 'primary',
    'bg-green-200 hover:bg-green-500 text-black': props.buttonType === 'secondary'
  }">
    <slot />
  </button>
</template>