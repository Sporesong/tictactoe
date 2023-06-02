<script setup lang="ts">
    import gridButton from "./gridButton.vue";
    import { defineProps, ref, defineEmits } from 'vue';

    const props = defineProps({
        gameOver: null
    });

    const emit = defineEmits(["click"]);
    const gameBoard = ref<Array<String | null>>(Array(9).fill(null));
    const playerSymbol = ref<String>("X");
    
    const clickGridButton = (index: number) => {
        const gameBoardCopy = gameBoard.value.slice();
        gameBoardCopy[index] = playerSymbol.value;
        gameBoard.value = gameBoardCopy;
        playerSymbol.value = playerSymbol.value === "X" ? "O": "X";
        emit("click", gameBoard.value);
    }

</script>

<template>
     <h1>Next turn: {{ playerSymbol }}</h1>
    <div class="gameBoard">
      <gridButton v-for="(gridButton, index) in gameBoard"
        :key="`gridButton-${index}`"
        :label="`gridButton-${index}`"
        :gameOver="gameOver"
        @click="clickGridButton(index)"/>
    </div>
  </template>

<style scoped>
    
    .gameBoard {
        position: relative;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(3, 1fr);
        background: rgb(34,193,195);
        background: linear-gradient(0deg, rgba(34,193,195,1) 0%, rgba(253,187,45,1) 100%);
        padding: 10px;
    }

</style>