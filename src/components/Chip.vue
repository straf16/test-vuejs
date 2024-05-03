<script setup>
const props = defineProps(['text'])
</script>

<template>
  <div class="rounded-full border border-white py-1 px-3 text-white text-sm whitespace-nowrap cursor-pointer">
    {{ props.text }}
  </div>
</template>