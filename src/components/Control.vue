<template>
  <div class="flex flex-row justify-center p-4 space-x-4">
    <div class="flex">
      <button
        @click="$emit('simulation-control')"
        :class="[simulationProcess ? 'bg-red-600' : 'bg-green-600']"
        class="px-2 py-1 text-white rounded-sm"
      >
        {{simulationProcess ? 'Pause' : 'Start'}}
      </button>
    </div>
    <div class="flex">
      <button
        @click="$emit('creset')"
        :class="[currentCycle ? 'bg-yellow-600' : 'bg-red-600']"
        class="px-2 py-1 text-white rounded-sm"
      >
        {{currentCycle ? 'Reset' : 'Clear'}}
      </button>
    </div>

  </div>
</template>

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
