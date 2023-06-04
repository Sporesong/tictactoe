<script setup lang="ts">
    import gridButton from "./gridButton.vue";
    import { defineProps, ref } from 'vue';

    interface IplayerNames {
        nameX: String,
        nameO: String
    };

    const props = defineProps<IplayerNames>();

    let gameBoard = ref<Array<String | null>>(Array(9).fill(null));
    const boardSize = 9;
    const playerSymbol = ref<String>("");
    let gameResult = "";
    
    function clickGridButton(index: number) {
        const gameBoardCopy = gameBoard.value.slice();
        playerSymbol.value = playerSymbol.value === "X" ? "O": "X";
        gameBoardCopy[index] = playerSymbol.value;
        gameBoard.value = gameBoardCopy;
        calculateWinner();     
    }

    function calculateWinner() {
        const lines = [
            [0, 1, 2],
            [3, 4, 5],
            [6, 7, 8],
            [0, 3, 6],
            [1, 4, 7],
            [2, 5, 8],
            [0, 4, 8],
            [2, 4, 6],
        ];

        for (let i = 0; i < lines.length; i++) {
            const [a, b, c] = lines[i];
            if (
            gameBoard.value[a] &&
            gameBoard.value[a] === gameBoard.value[b] &&
            gameBoard.value[a] === gameBoard.value[c]
            ) {   
                gameResult = `${gameBoard.value[a]} Wins`;
                return;  
            }
        }

        if (gameBoard.value.every((val) => val)) {
            gameResult ="Tie!";
            return;
        }
    };

    function startNewGame() {
        //försökte kalla på reset i gridButton med definExpose men lyckas inte.
        gameResult = "";
        playerSymbol.value = "X";
    }

</script>

<template>
     <h1 v-if="!gameResult" >Next turn: {{ playerSymbol === "X" ? nameX : nameO }} </h1>
     <button v-else @click="startNewGame">Start new game</button>
    <div class="gameBoard">
      <gridButton v-for="n in boardSize"
        :key="`gridButton-${n}`"
        :label="`gridButton-${n}`"
        @click="clickGridButton(n)"
        :turn="playerSymbol"
        :gameOver="gameResult ? true : false"/>
    </div>
    <h1>{{ gameResult }}</h1>
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