<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
    name: String,
    disabled: Boolean
});

const value = "";
const gameOver = false;

</script>

<template>
    <button class="gridButton" :name="name" :disabled="gameOver || value">
    {{ value }}
    </button>
</template>

<style scoped>
.gridButton {
  background: #ffffff;
  height: 22vmin;
  width: 22vmin;
  border: none;
  border-radius: 8px;
  font-size: 12vmin;
  color: #d161ff;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
}

</style>