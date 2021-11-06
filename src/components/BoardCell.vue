<template>
  <span
    @click="$emit('cell-click', cellNumber)"
    :class="[cellState ? 'bg-white' : 'bg-black']"
    class="flex flex-row p-2.5 border border-solid border-white"
  ></span>
</template>

<script setup>
const props = defineProps({
  cellNumber: {
    type: Number,
  },
  cellState: {
    type: Boolean,
  },
});
</script>
