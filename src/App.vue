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
const initialBoardState = ref(new Set());
const boardState = ref(new Set());

onMounted(() => {
  setInterval(() => {
    if (simulationProcess.value) {
      cycle();
    }
  }, 350);
});

function cycle() {
  const surrounding = getSurroundingOfCurrentlyAliveCell([...boardState.value]);
  const toBeChecked = new Set([...surrounding, ...boardState.value]);

  setCellNextCycle(toBeChecked);
  currentCycle.value++;
}

function getSurroundingOfCurrentlyAliveCell(cells) {
  const surrounding = new Set();
  const boardFullSize = board.value.width * board.value.height;

  cells.forEach((cell) => {
    const left = cell - 1;
    const right = cell + 1;

    if (left > 0 && cell % board.value.width !== 1) {
      surrounding.add(left);
    }
    if (right < boardFullSize && cell % board.value.width !== 0) {
      surrounding.add(right);
    }

    const up = cell - board.value.width;
    const upLeft = up - 1;
    const upRight = up + 1;

    if (up > 0) {
      surrounding.add(up);
      if (up % board.value.width !== 1) {
        surrounding.add(upLeft);
      }
      if (up % board.value.width !== 0) {
        surrounding.add(upRight);
      }
    }

    const down = cell + board.value.width;
    const downLeft = down - 1;
    const downRight = down + 1;

    if (down < boardFullSize) {
      surrounding.add(down);
      if (down % board.value.width !== 1) {
        surrounding.add(downLeft);
      }
      if (down % board.value.width !== 0) {
        surrounding.add(downRight);
      }
    }
  });

  return new Set(surrounding);
}

function setCellNextCycle(pendingCheck) {
  const willBeAlive = new Set();

  pendingCheck.forEach((cell) => {
    const surroundingAlive = getSurroundingOfCurrentlyAliveCell([cell]);

    const intersect = new Set(
      [...surroundingAlive].filter((x) => boardState.value.has(x))
    );

    if (intersect.size === 3) {
      willBeAlive.add(cell);
    }
    if (boardState.value.has(cell) && intersect.size === 2 || intersect.size === 3) {
      willBeAlive.add(cell)
    }
  });

  boardState.value = willBeAlive;
}

function cellClick(cellNum) {
  if (boardState.value.has(cellNum)) {
    boardState.value.delete(cellNum);
    console.log(`cell ${cellNum} removed`);
  } else {
    boardState.value.add(cellNum);
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
  }
  simulationProcess.value = !simulationProcess.value;
}

function clearOrReset() {
  console.log("creset");
  if (currentCycle.value !== 0) {
    currentCycle.value = 0;
    boardState.value = initialBoardState.value;
  } else {
    boardState.value.clear();
  }
}
</script>
