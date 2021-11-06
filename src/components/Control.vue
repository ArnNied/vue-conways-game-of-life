<script setup>
const props = defineProps({
  simulationProcess: {
    type: Boolean,
    default: false,
  },
  currentCycle: {
    type: Number,
    default: 0,
  },
});
</script>

<template>
  <div class="flex flex-row justify-center p-4 space-x-4">
    <div class="flex">
      <button
        @click="$emit('simulation-control')"
        class="p-2 bg-gray-900 text-white rounded"
      >
        {{simulationProcess ? 'Pause' : 'Start'}}
      </button>
    </div>
    <div class="flex">
      <button
        @click="$emit('creset')"
        class="p-2 bg-gray-900 text-white rounded"
      >
        {{currentCycle ? 'Reset' : 'Clear'}}
      </button>
    </div>

  </div>
</template>