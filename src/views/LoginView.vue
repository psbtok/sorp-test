<template>
  <div class="login-container">
    <PasswordDisplay :currentPassword="currentPassword" />
    <div class="button-container">
      <NumberPad @enter="handleEnter" @clear="handleClear" @deleteLast="handleDeleteLast" />
      <ConfirmButton class="confirm-button" word="Continue" />
    </div>
  </div>
</template>

<style>
  .login-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 100vw;
    height: 100vh;
    padding: 1em;
  }

  .confirm-button {
    margin-top: 0.5em;
  }
</style>

<script setup lang="ts">
import { ref } from 'vue';
import PasswordDisplay from '@/components/PasswordDisplay.vue';
import NumberPad from '@/components/NumberPad.vue';
import ConfirmButton from '@/components/ConfirmButton.vue';

const currentPassword = ref(''); 

const handleEnter = (number) => {
  if (number === 'X') {
    return; 
  }
  currentPassword.value += number;
  console.log('Current Password:', currentPassword.value);
};

const handleClear = () => {
  currentPassword.value = '';
  console.log('Cleared input');
};

const handleDeleteLast = () => {
  currentPassword.value = currentPassword.value.slice(0, -1);
  console.log('Deleted last entry:', currentPassword.value);
};
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
