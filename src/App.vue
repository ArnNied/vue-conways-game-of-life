<script setup>
import { ref } from "vue";

import Board from "/src/components/Board.vue";
import Config from "/src/components/Config.vue";
import Control from "/src/components/Control.vue";
import Header from "/src/components/Header.vue";

const config = ref(null);

const simulationProcess = ref(false);
const currentCycle = ref(0);

function simulationControl() {
  console.log("simulationProcess");
  simulationProcess.value = !simulationProcess.value;
}

function clearOrReset() {
  console.log("creset");
}
</script>

<template>
  <div class="flex flex-col">
    <Header />
    <Config ref="config" />
    <Control
      @simulation-control="simulationControl"
      @creset="clearOrReset"
      :simulation-process="simulationProcess"
      :current-cycle="currentCycle"
    />
    <Board :config="config" />
  </div>
</template>

<style>
</style>
