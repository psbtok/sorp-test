<template>
  <button class="confirm-button" @click="emitClick">{{ word }}</button>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  word: {
    type: String,
    required: true
  }
});

const emit = defineEmits();

const emitClick = () => {
  emit('click');
};
</script>

<style scoped>
.confirm-button {
  width: 100%;
  height: 20vw;
  font-size: 1.1em;
  border-radius: 1em;
  background-color: var(--highlight-blue);
  color: white;
  border: 2px solid var(--highlight-blue);
  cursor: pointer;
  transition-duration: 0.3s;
}

.confirm-button:active {
  background-color: white;
  color: var(--highlight-blue);
}
</style>
