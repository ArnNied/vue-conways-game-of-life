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
      :board-state="boardState"
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
const boardState = ref([]);

function cellClick(cellNum) {
  if (boardState.value.includes(cellNum)) {
    boardState.value = boardState.value.filter((val) => val !== cellNum);
    console.log(`cell ${cellNum} removed`);
  } else {
    boardState.value.push(cellNum);
    console.log(`cell ${cellNum} added`);
  }
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
