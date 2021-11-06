<script setup>
import { ref } from "vue";

import Board from "/src/components/Board.vue";
import Config from "/src/components/Config.vue";
import Header from "/src/components/Header.vue";

const config = ref(null);
</script>

<template>
  <div class="flex flex-col">
    <Header />
    <Config ref="config" />
    <Board :config="config" />
  </div>
</template>

<style>
</style>
