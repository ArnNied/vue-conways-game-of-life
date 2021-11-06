<script setup>
import { ref } from "vue";

const board = ref({ width: 0, height: 0 });
const localBoard = ref({ width: 30, height: 10 });

function createBoard() {
  board.value.width = localBoard.value.width;
  board.value.height = localBoard.value.height;
}

defineExpose({
  board,
});
</script>

<template>
  <form
    @submit.prevent="createBoard"
    class="flex flex-row justify-center p-8 space-x-8"
  >
    <div class="flex flex-row items-center space-x-2">
      <p class="text-white">Width:</p>
      <input
        v-model="localBoard.width"
        type="number"
        name="config-width"
        id="config-width"
        placeholder="Board Width"
        class="p-1 rounded-sm"
      />
    </div>
    <div class="flex flex-row items-center space-x-2">
      <p class="text-white">Height:</p>
      <input
        v-model="localBoard.height"
        type="number"
        name="config-height"
        id="config-Height"
        placeholder="Board Height"
        class="p-1 rounded-sm"
      />
    </div>
    <div class="flex items-center">
      <button
        type="submit"
        class="p-2 bg-gray-800 text-white"
      >
        Build
      </button>
    </div>
  </form>
</template>
