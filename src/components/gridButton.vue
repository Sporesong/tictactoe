<script setup lang="ts">
import { defineEmits, ref } from 'vue';

/* const props = defineProps({
    name: String,
    value: {
        type: String,
        default: "",
    },
    gameOver: null
});
 */

let buttonValue = ref("");

const emit = defineEmits(["click"]);

function clickGridButton() {
    //emit("click", "index");
    buttonValue.value = buttonValue.value === "X" ? "O": "X";
    console.log(buttonValue.value);
    
};  

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