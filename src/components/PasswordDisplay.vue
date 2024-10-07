<template>
  <div class="password-display">
    <div></div>
    <label>Enter admin password:</label>
    <div class="password-info">
      <span class="password-hidden" v-if="!isPasswordVisible">{{ maskedPassword }}</span>
      <span v-else>{{ currentPassword }}</span>
      <button @click="togglePasswordVisibility">
        {{ isPasswordVisible ? 'Hide' : 'Show' }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.password-display {
  display: flex;
  flex-direction: column;
  justify-content: center;
  background: white;
  width: 100%;
  border-radius: 0.4em;
  height: 20vw;
  padding: 8px 16px;
}

span {
  letter-spacing: 8px;
}

.password-info {
  display: flex;
  height: 22px;
  justify-content: space-between;
}

label {
  font-size: 0.8em;
  margin-bottom: 4px;
  color: var(--regular-grey);
}

.password-hidden {
  position: relative;
  top: 3px;
  letter-spacing: 10px;
}

button {
  color: var(--regular-grey);
  background: none;
  text-decoration: underline;
}
</style>

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
