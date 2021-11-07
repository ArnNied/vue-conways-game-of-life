<template>
  <div class="flex flex-row justify-center p-4 space-x-4">
    <div class="flex">
      <button
        @click="$emit('simulation-control')"
        :class="[
          simulationProcess ?
          'bg-red-600 hover:bg-red-700 focus:bg-red-800' :
          'bg-green-600 hover:bg-green-700 focus:bg-green-800'
        ]"
        class="px-2 py-1 text-white rounded-sm"
      >
        {{simulationProcess ? 'Pause' : 'Start'}}
      </button>
    </div>
    <div class="flex">
      <button
        @click="$emit('creset')"
        :class="[
          currentCycle ?
          'bg-yellow-600 hover:bg-yellow-700 focus:bg-yellow-800' :
          'bg-red-600 hover:bg-red-700 focus:bg-red-800'
        ]"
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
