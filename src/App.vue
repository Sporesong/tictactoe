<script setup lang="ts">
  import gameBoard from "./components/gameBoard.vue";
  import setPlayers from "./components/setPlayers.vue";
  import { onMounted, ref } from "vue";
  let playersSet = ref(false);

  onMounted(() => {
    const handlePlayersSet = () => {
      playersSet.value = true;
    }
  });

</script>

<template>
  <div class="gameContainer">
    <setPlayers v-if="!playersSet" @playersSet="handlePlayersSet"></setPlayers>
    <gameBoard v-else></gameBoard>
  </div>
</template>

<style scoped>

</style>
