<template>
  <span
    @click="handleClick"
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

const cellState = ref(false);

function handleClick() {
  console.log(props.cellNumber);
  cellState.value = !cellState.value;
}
</script>
