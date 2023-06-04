<script setup lang="ts">
  import { defineEmits, ref } from 'vue';
import GameBoard from './gameBoard.vue';

  defineExpose({
    reset,
  });

  let buttonValue = ref("");

  const emit = defineEmits(["click"]);

  interface IgridButton {
    gameOver: String,
    turn: String ;
  };

  const props = defineProps<IgridButton>();

  function clickGridButton() {
    if(props.gameOver) {
      return;
    }
    buttonValue.value = props.turn === "X" ? "X": "O";
      emit("click", "index");
  };  

  function reset() {
    buttonValue.value = "";
  }

</script>

<template>
    <button class="gridButton" @click="clickGridButton">
      {{ buttonValue }}
    </button>
  </template>

<style scoped>
.gridButton {
  background: #ffffff;
  height: 23vmin;
  width: 22vmin;
  border: none;
  border-radius: 8px;
  font-size: 4rem;
  color: #2f0341;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  margin: 10px;
  padding: 0;
}

</style>