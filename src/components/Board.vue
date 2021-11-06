<script setup>
import BoardCell from "/src/components/BoardCell.vue";

const props = defineProps({
  config: {
    type: Object,
  },
});
</script>

<template>
  <div
    v-for="i in config.board.height"
    :key="i"
    class="flex flex-row"
  >
    <BoardCell
      v-for="j in config.board.width"
      :key="j"
      :cellNumber="(i - 1) * config.board.width + j"
    />
  </div>
</template>
