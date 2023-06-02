<script setup lang="ts">
    import { defineComponent, ref } from "vue"; 
    import gridButton from "./gridButton.vue";

    const gameBoard = ref(Array(9).fill(null));
    const playerSymbol = ref("X"); 

</script>

<template>
    <div class="gameBoard">
        <gridButton></gridButton>
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
    }

</style>