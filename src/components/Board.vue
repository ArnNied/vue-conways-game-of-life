<script setup>
import BoardCell from "/src/components/BoardCell.vue";

const props = defineProps({
  config: {
    type: Object,
  },
});
</script>

<template>
  <div class="flex flex-col mx-auto">
    <div
      v-for="i in config.board.height"
      :key="i"
      class="flex flex-row"
    >
      <BoardCell
        v-for="j in config.board.width"
        :key="(i - 1) * config.board.width + j"
        :cellNumber="(i - 1) * config.board.width + j"
      />
    </div>
  </div>

</template>
