<template>
  <div class="flex flex-col">
    <div class="
			flex flex-row
			items-center
			p-4
			bg-gray-800
			justify-center
			space-x-2
		">
      <img
        src="/src/assets/logo.png"
        alt="Vue logo"
        class="w-16 h-16"
      />
      <h2 class="font-bold text-2xl text-white">Conway's Game of Life</h2>
    </div>
    <div class="flex flex-row justify-center p-1 bg-gray-700 space-x-8">
      <a
        href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life"
        target="_blank"
        class="text-sm text-white hover:underline"
      >
        What is "John Conway's Game of Life"?
      </a>
      <a
        href="https://github.com/ArnNied/vue-conways-game-of-life"
        target="_blank"
        class="text-sm text-white hover:underline"
      >
        Source Code
      </a>
    </div>
  </div>
</template>
