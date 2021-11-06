<template>
  <span
    @click="cellClick(cellNumber)"
    :class="[cellState ? 'bg-white' : 'bg-black']"
    class="flex flex-row p-2.5 border border-solid border-white"
  ></span>
</template>

<script setup>
import { ref } from "@vue/reactivity";

const props = defineProps({
  cellNumber: {
    type: Number,
  },
});

const emit = defineEmits(["cell-click"]);

const cellState = ref(false);

function cellClick(cellNum) {
  cellState.value = !cellState.value;
  emit("cell-click", cellNum);
}
</script>
