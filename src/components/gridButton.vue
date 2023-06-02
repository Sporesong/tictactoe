<script setup lang="ts">
import { defineProps, ref, defineEmits } from 'vue';

const props = defineProps({
    name: String,
    value: {
        type: String,
        default: "",
    },
    gameOver: null
});

const emit = defineEmits(["click"]);

const clickGridButton = (index: number) => {
    emit("click", "index");
};  

</script>

<template>
    <button class="gridButton" :name="name" :disabled="gameOver || value">
      {{ value }}
    </button>
  </template>

<style scoped>
.gridButton {
  background: #ffffff;
  height: 23vmin;
  width: 22vmin;
  border: none;
  border-radius: 8px;
  font-size: 2rem;
  color: #2f0341;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  margin: 10px;
}

</style>