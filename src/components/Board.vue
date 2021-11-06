<script setup>
import BoardCell from "/src/components/BoardCell.vue";

const props = defineProps({
  board: {
    type: Object,
  },
});
</script>

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
      />
    </div>
  </div>
</template>
