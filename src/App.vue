<script setup lang="ts">
  import gameBoard from "./components/gameBoard.vue";
  import setPlayers from "./components/setPlayers.vue";
  import  { ref } from "vue";

  let playersSet = ref(false);
  let playerXName:String = "";
  let playerOName:String = "";
  
  function handlePlayersSet(playerX:String, playerO:string) {
    playersSet.value = true;
    playerXName = playerX;
    playerOName = playerO;
  }

</script>

<template>
  <div class="gameContainer">
    <setPlayers v-if="!playersSet" @playersSet="handlePlayersSet"></setPlayers>
    <gameBoard v-else :nameX="playerXName" :nameO="playerOName"></gameBoard>
  </div>
</template>

<style scoped>

</style>
