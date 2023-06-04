<script setup lang="ts">
    import { defineEmits } from "vue";

    const emits = defineEmits(["playersSet"]);
    let playerX = "";
    let playerO = "";

    function startGame() {
        emits("playersSet", playerX, playerO);        
    }
</script>

<template>
    <h1>Set player names</h1>
    <form class="playerNameForm" @submit.prevent="startGame">
        <input v-model="playerX" type="text" placeholder="Player X" required>
        <input v-model="playerO" type="text" placeholder="Player O" required>
        <input type="submit" class="button">
    </form>
</template>

<style scoped>

</style>