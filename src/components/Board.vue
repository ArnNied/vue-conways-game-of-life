<template>
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
        @cell-click="cellClick"
      />
    </div>
  </div>
</template>

<script setup>
import BoardCell from "/src/components/BoardCell.vue";

const props = defineProps({
  board: {
    type: Object,
  },
});

const emit = defineEmits(["cell-click"]);

function cellClick(cellNum) {
  emit("cell-click", cellNum);
}
</script>
