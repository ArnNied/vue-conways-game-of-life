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
      @cell-click="cellClick"
      :board="board"
      :board-state="boardState"
      :currentCycle="currentCycle"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

import Board from "/src/components/Board.vue";
import Config from "/src/components/Config.vue";
import Control from "/src/components/Control.vue";
import Header from "/src/components/Header.vue";

const board = ref({ width: 0, height: 0 });
const simulationProcess = ref(false);
const currentCycle = ref(0);
const initialBoardState = ref([]);
const boardState = ref([]);

onMounted(() => {
  setInterval(() => {
    if (simulationProcess.value) {
      console.log("cycle");
      currentCycle.value += 1;
    }
  }, 350);
});

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
  if (currentCycle.value === 0) {
    initialBoardState.value = boardState.value;
    console.log(initialBoardState.value);
  }
  simulationProcess.value = !simulationProcess.value;
}

function clearOrReset() {
  console.log("creset");
  if (currentCycle.value !== 0) {
    currentCycle.value = 0;
    boardState.value = initialBoardState.value;
  } else {
    boardState.value = [];
  }
}
</script>
