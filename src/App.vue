<template>
  <div class="flex flex-col">
    <Header />
    <Config @board-create="boardCreate" />
    <Control
      @simulation-control="simulationControl"
      @creset="clearOrReset"
      :simulation-process="simulationProcess"
      :current-cycle="currentCycle"
    />
    <Board
      :board="board"
      @cell-click="cellClick"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";

import Board from "/src/components/Board.vue";
import Config from "/src/components/Config.vue";
import Control from "/src/components/Control.vue";
import Header from "/src/components/Header.vue";

const board = ref({ width: 0, height: 0 });
const simulationProcess = ref(false);
const currentCycle = ref(0);

function cellClick(cellNumber) {
  console.log(cellNumber);
}

function boardCreate(size) {
  board.value.width = size.width;
  board.value.height = size.height;
}

function simulationControl() {
  console.log("simulationProcess");
  simulationProcess.value = !simulationProcess.value;
}

function clearOrReset() {
  console.log("creset");
}
</script>
