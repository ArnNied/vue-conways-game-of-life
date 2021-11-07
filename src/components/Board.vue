<template>
  <div class="flex flex-col">
    <h2 class="flex mx-auto text-white">Cycle: {{currentCycle}}</h2>
    <div class="flex flex-col mx-auto p-4">
      <div
        v-for="i in board.height"
        :key="i"
        class="flex flex-row"
      >
        <BoardCell
          v-for="j in board.width"
          :key="(i - 1) * board.width + j"
          :cellNumber="(i - 1) * board.width + j"
          :cellState="boardState.has((i - 1) * board.width + j) ? true : false"
          @cell-click="cellClick"
        />
      </div>
    </div>
  </div>

</template>

<script setup>
import BoardCell from "/src/components/BoardCell.vue";

const props = defineProps({
  board: {
    type: Object,
  },
  boardState: {
    type: Set,
  },
  currentCycle: {
    type: Number,
  },
});

const emit = defineEmits(["cell-click"]);

function cellClick(cellNum) {
  emit("cell-click", cellNum);
}
</script>
