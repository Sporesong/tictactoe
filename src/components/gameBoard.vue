<script setup lang="ts">
    import gridButton from "./gridButton.vue";
    import { defineProps, onMounted, ref } from 'vue';

    interface IplayerNames {
        nameX: String,
        nameO: String
    };

    const props = defineProps<IplayerNames>();

    let gameBoard = ref<Array<String | null>>(Array(9).fill(null));
    const boardSize = 9;
    const playerSymbol = ref<String>("X");
    let gameResult = ref("");
    const btnRefs = ref();
    
    function clickGridButton(index: number) {
        const gameBoardCopy = gameBoard.value.slice();
        gameBoardCopy[index] = playerSymbol.value;
        playerSymbol.value = playerSymbol.value === "X" ? "O": "X";
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
                gameResult.value = `${gameBoard.value[a]} Wins`;
                return;  
            }
        }

        if (gameBoard.value.every((val) => val)) {
            gameResult.value ="Tie!";
            return;
        }
    };

    function startNewGame() {
        //försökte kalla på reset i gridButton med definExpose men lyckas inte.
        
        for(let i = 0; i < boardSize; i++) {
            btnRefs.value[i].reset();
        }
        gameResult.value = "";
        playerSymbol.value = "X";
        gameBoard.value = Array(9).fill(null);
    }   

</script>

<template>
    <h1 v-if="!gameResult" >Player {{ playerSymbol === "X" ? nameX : nameO }}'s turn</h1>
    <button v-else @click="startNewGame">Start new game</button>
    <div class="gameBoard">
      <gridButton v-for="index in boardSize"
        :key="`gridButton-${index-1}`"
        :label="`gridButton-${index-1}`"
        @click="clickGridButton(index-1)"
        :turn="playerSymbol"
        :gameOver="gameResult"
        ref="btnRefs"/>
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