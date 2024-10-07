<template>
  <button class="confirm-button" @click="handleClick">{{ word }}</button>
</template>


<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
  word: {
    type: String,
    required: true
  }
});

const handleClick = () => {
  console.log(`${props.word} button clicked!`);
};
</script>

<style scoped>
.confirm-button {
  width: 100%;
  height: 20vw;
  font-size: 1.25em;
  border-radius: 1em;
  background-color: #3448F0;
  color: white;
  border: none;
  cursor: pointer;
}

.confirm-button:hover {
  background-color: #4E46B4;
}
</style>
