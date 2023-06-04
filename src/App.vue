<script setup lang="ts">
  import gameBoard from "./components/gameBoard.vue";
  import setPlayers from "./components/setPlayers.vue";
  import  { ref } from "vue";

  let playersSet = ref(false);
  
  function handlePlayersSet() {
    playersSet.value = true;
    console.log(playersSet);
  }

</script>

<template>
  <div class="gameContainer">
    <setPlayers v-if="!playersSet" @playersSet="handlePlayersSet"></setPlayers>
    <gameBoard v-else></gameBoard>
  </div>
</template>

<style scoped>

</style>
