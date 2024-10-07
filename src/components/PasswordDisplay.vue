<template>
  <div class="password-display">
    <label>Enter admin password:</label>
    <div>
      <span v-if="!isPasswordVisible">{{ maskedPassword }}</span>
      <span v-else>{{ currentPassword }}</span>
      <button @click="togglePasswordVisibility">
        {{ isPasswordVisible ? 'Hide' : 'Show' }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps, computed } from 'vue';

const props = defineProps({
  currentPassword: {
    type: String,
    required: true
  }
});

const isPasswordVisible = ref(false);
const maskedPassword = computed(() => '*'.repeat(props.currentPassword.length));

const togglePasswordVisibility = () => {
  isPasswordVisible.value = !isPasswordVisible.value;
};
</script>

<style scoped>
.password-display {
  margin-bottom: 20px;
}

button {
  margin-left: 10px;
}
</style>
