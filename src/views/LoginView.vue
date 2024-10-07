<template>
  <div class="login-container">
    <PasswordDisplay :currentPassword="currentPassword" />
    <div class="button-container">
      <NumberPad @enter="handleEnter" @clear="handleClear" @deleteLast="handleDeleteLast" />
      <ConfirmButton 
        @click="validatePassword"
        class="confirm-button" 
        word="Continue" 
      />
    </div>
  </div>
</template>

<style>
  .login-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 100%;
    padding: 1em;
    padding-bottom: 1.5em;
  }

  .confirm-button {
    margin-top: 0.5em;
  }
</style>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import PasswordDisplay from '@/components/PasswordDisplay.vue';
import NumberPad from '@/components/NumberPad.vue';
import ConfirmButton from '@/components/ConfirmButton.vue';

const router = useRouter();
const currentPassword = ref('');

const handleEnter = (number: string | number) => {
  if (number === 'X') {
    return; 
  }
  currentPassword.value += number;
};

const handleClear = () => {
  currentPassword.value = '';
};

const handleDeleteLast = () => {
  currentPassword.value = currentPassword.value.slice(0, -1);
};

const validatePassword = () => {
  if (currentPassword.value.length > 0) {
    router.push('/home/');
  }
};
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
