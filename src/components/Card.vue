<script setup>
const props = defineProps(['name', 'price'])
</script>

<template>
  <div class="flex flex-col rounded-lg border border-blackgap-2">
    <img src="https://placehold.co/400x300" />
    <span class="text-base p-2">{{ props.name }}</span>
    <div class="flex justify-between p-2 mt-auto">
      <span class="text-sm">{{  props.price }}</span>
      <span class="text-xs bg-orange-400 rounded p-1 text-white">1x</span>
    </div>
  </div>
</template>