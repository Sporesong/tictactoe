<script setup lang="ts">
  import { defineEmits, ref } from 'vue';

  let buttonValue = ref("");

  const emit = defineEmits(["click"]);

  interface IgridButton {
    turn: String ;
  };

  const props = defineProps<IgridButton>();

  function clickGridButton() {
    buttonValue.value = props.turn === "X" ? "O": "X";
      emit("click", "index");
  };  

</script>

<template>
    <button class="gridButton" @click.once="clickGridButton">
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