<template>
  <div class="number-pad">
    <div class="buttons">
      <div class="row" v-for="(row, index) in groupedNumbers" :key="index">
        <button v-for="num in row" :key="num" @click="enterNumber(num)">
          <span>{{ num }}</span>
        </button>
      </div>
      <div class="row">
        <button @click="clear">X</button>
        <button @click="enterNumber(0)">0</button>
        <button @click="deleteLast">←</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .number-pad {
      display: flex;
      flex-direction: column;
    }

  .buttons {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
  }

  .row {
    display: flex;
    gap: 0.5em;
  }

  button {
    width: 28vw;
    height: 20vw;
    display: flex;
    justify-content: center;
    align-items: center;
    background: white;
    border: 2px solid white;
    border-radius: 1em;
    transition-duration: 0.2s;
    color: var(--highlight-blue);

    font-size: 1.25em;
  }

  span {
    font-size: 0.8em;
    font-weight: 500;
    transition-duration: 0.2s;
    font-size: 1em;
  }

  button:active {
    border-color: var(--highlight-blue);

    span {
      font-size: 0.9em;
    }
  }
</style>

<script setup lang="ts">
import { ref, defineEmits, computed } from 'vue';

const emit = defineEmits<{
  (e: 'enter', number: number): void;
  (e: 'clear'): void;
  (e: 'deleteLast'): void;
}>();

const numbers = ref([1, 2, 3, 4, 5, 6, 7, 8, 9]);

const groupedNumbers = computed(() => {
  const rows = [];
  for (let i = 0; i < numbers.value.length; i += 3) {
    rows.push(numbers.value.slice(i, i + 3));
  }
  return rows;
});

const enterNumber = (number: number) => {
  emit('enter', number);
};

const clear = () => {
  emit('clear');
};

const deleteLast = () => {
  emit('deleteLast');
};
</script>