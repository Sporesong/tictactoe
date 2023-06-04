<script setup lang="ts">
    import { ref, defineEmits } from "vue";

    const emit = defineEmits(["playersSet"]);
    const playerX = ref("");
    const playerO = ref("");

    function strartGame() {
        const playersSet = true;
        emit("playersSet", playersSet);    
    }
</script>

<template>
    <h1>Set player names</h1>
    <form class="playerNameForm" @submit.prevent="strartGame">
        <input v-model="playerX" type="text" placeholder="Player X" required>
        <input v-model="playerO" type="text" placeholder="Player O" required>
        <input type="submit" class="button">
    </form>
</template>

<style scoped>

</style>